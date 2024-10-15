<svelte:head>
    <link href="/css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="/css/site.css" rel="stylesheet" />
    <script src="/js/bootstrap.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Port+Lligat+Slab&display=swap" rel="stylesheet">
    <title>{title} | Todd Makes Games!</title>
</svelte:head>

<script lang="ts">
    import Contact from "../components/contact.svelte";
    import Portfolio from "../components/portfolio.svelte";
    import MailingList from "../components/mailinglist.svelte";

    let title: string = 'Hello!';
    let page: string = 'portfolio';

    function changePage(newPage: string) {
        page = newPage;
        if (page === 'portfolio') {
            title = 'Hello!';
        } else if (page === 'contact') {
            title = 'Are you ready?';
        } else if (page === 'mailing') {
            title = 'Mailing List';
        }
    }

</script>

<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container-fluid">
        <a class="navbar-brand" href="/">
            <img src="/images/me-gameboy-lg.png" alt="Hey, that's me!" width="30">
        </a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse"
            data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent"
            aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mx-auto">
                <li class="nav-item">
                    <a class="nav-link" href="/" on:click={function() { changePage('portfolio'); }}>Portfolio</a>
                </li>
                
                <li class="nav-item">
                    <a class="nav-link" href="/" on:click={function () { changePage('mailing'); }}>Mailing List</a>
                </li>

                <li class="nav-item">
                    <a class="nav-link" href="/" on:click={function () { changePage('contact'); }}>Contact Me</a>
                </li>
            </ul>
        </div>
    </div>
</nav>

<div class="content px-4" style="margin-bottom: 50px;">
    {#if page === 'portfolio'}
        <Portfolio />
    {:else if page === 'contact'}
        <Contact />
    {:else if page === 'mailing'}
        <MailingList />
    {/if}
</div>

<footer class="bg-dark text-center text-lg">
    <div class="container p-4">
        <p>Copyright &copy; {new Date().getFullYear()} Todd Gibson</p>
    </div>
</footer>
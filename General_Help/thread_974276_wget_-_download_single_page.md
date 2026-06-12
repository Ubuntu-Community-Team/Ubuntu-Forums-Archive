---
title: "wget - download single page"
date: 2008-11-07
forum: General Help
---

### Post by suggsjc on 2008-11-07
I'm having troubles getting the exact syntax down for a wget command.  I am wanting to download a **single** page and all of its dependencies (css, images, etc) into a **single** directory (not a directory for each subdomain) and have the target page named index.html

So that if the following page was located at [http://example.com/some/path/pageIwant.php](http://example.com/some/path/pageIwant.php)
[HTML]<html>
<head>
<link rel="stylesheet" href="http://static.example.com/style.css" />
<script type="text/javascript" src="../js/main.js"></script>
</head>
<body>
<h1>Hello World!</h1>
<img src="http://images.example.com/img/kitty.jpg" />
</body>
</html>[/HTML]

I want to be able to do
```
wget [options] http://example.com/some/path/pageIwant.php
```
and have the following in a directory that I specify (say "/archives/1/") and I would get the following output so that if I were to look at the index.html page locally it would look exactly like the example.com page.

```
user$ ls /archives/1/
index.html
kitty.jpg
main.js
style.css
```

Let me know if that doesn't make sense or if you need any more information.  Also, it doesn't necessarily have to be wget either, that is just what seems like it would be the best solution...but I am up for any suggestions.

---

### Post by suggsjc on 2008-11-10
Bump...

If there is a better place (forum) to ask this that would be helpful too

---


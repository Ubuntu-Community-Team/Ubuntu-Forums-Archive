---
title: "rTWi (web interface for rTorrent): problems"
date: 2008-07-17
forum: General Help
---

### Post by adcwoef on 2008-07-17
Hi

I have been trying thw whole day to get the web interface for rTorrent called rTWi to work and it does run but there are some major problems left. I have followed the [official install instructions]("http://projects.cyla.homeip.net/rtwi/wiki/InstallationGuide") at the projects wiki and compiled rTorrent with xmlrpc-c support and everything. I can log in to the rTWi interface and see the GUI but at the top there are some error messages:

```


Warning: DOMDocument::loadXML() [function.DOMDocument-loadXML]: Empty string supplied as input in /var/www/rtorrent/includes/classes/xmlrpc_handler.inc.php on line 137

Warning: Invalid argument supplied for foreach() in /var/www/rtorrent/includes/classes/xmlrpc_handler.inc.php on line 427

Warning: Invalid argument supplied for foreach() in /var/www/rtorrent/index.php on line 381

Warning: DOMDocument::loadXML() [function.DOMDocument-loadXML]: Empty string supplied as input in /var/www/rtorrent/includes/classes/xmlrpc_handler.inc.php on line 137

Warning: chdir() [function.chdir]: No such file or directory (errno 2) in /var/www/rtorrent/index.php on line 10

Warning: chdir() [function.chdir]: No such file or directory (errno 2) in /var/www/rtorrent/index.php on line 10

```

I don't understand these error messages so I don't not what to do to fix them. Any help to make me understand the problem and solve it is really appreciated. Thanks!

Screenshot (click to view)
[[img]http://img384.imageshack.us/img384/2068/rtwidc7.png[/img]](http://img503.imageshack.us/img503/6199/rtwiov0.png)

---

### Post by tutwabee on 2008-09-01
I am getting the same errors and I have not managed to fix it yet.

This may help though: [http://projects.cyla.homeip.net/rtwi/ticket/25]("http://projects.cyla.homeip.net/rtwi/ticket/25")

---

### Post by ramgine on 2008-12-14
I know this is an old thread, but the only thread i've found relating to my problem. Anyone come up with a solution? The link provided didn't fix it for me.

---

### Post by ramgine on 2008-12-16
help?

---


---
title: "test web pages in different screen resolutions"
date: 2008-09-03
forum: General Help
---

### Post by ghostandmachine on 2008-09-03
While making web pages i would like to test them in different screen resolutions (possibly even different browsers). I've searched google with no results. I've read about a service called BrowserCam but it'll cost me. Plus I'm looking for a open source alternative. Thanks in advance.

---

### Post by pytheas22 on 2008-09-03
[This site]("http://www.yournew.com/resolution_test.cfm") allows you to easily approximate what your pages look like at different resolutions.

If you need to be really serious, you could set up a virtual machine and test your pages inside it.  This has the added benefit (if you install Windows inside of your virtual machine) of allowing you to test your site in IE and other Windows-only browsers easily (you can run IE 5-7 on Linux in wine, but IE 7 in particular is still flaky that way...it's much more hassle-free to do it inside a virtual machine).

---

### Post by ghostandmachine on 2008-09-03
this is something of what I'm looking for but the only problem is the page already has to be uploaded to the internet. Is there a program or another website where it just loads it from my computer rather than from an internet address. Thanks though I've bookmarked the website.

---

### Post by pytheas22 on 2008-09-04
If you need the sites to be only on your local server, I don't know of any programs that can do that--your best bet, as far as I know, is to use a virtual machine, whose screen resolution you can change easily.

The other option, of course, is to connect your Apache server to the Internet and give that website just the IP of your server--I don't think you need a domain name to use that service, just an IP.

Someone else may have a better idea, though--I've never done very serious web development and have been happy enough just to use that online service for testing the few basic sites that I put together when need be.

---


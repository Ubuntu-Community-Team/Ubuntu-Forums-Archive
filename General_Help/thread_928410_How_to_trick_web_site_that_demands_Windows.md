---
title: "How to trick web site that demands Windows"
date: 2008-09-23
forum: General Help
---

### Post by zerubbabel on 2008-09-23
The chase.com web site that I use to manage my Chase Visa card will only give me access to my account when I connect from Windows, regardless of which browser I use. Works fine with Firefox 3 on Windows; doesn't work with Firefox 3 on Ubuntu Hardy. The Chase tech support say that Windows is a requirement to access their online banking. That seems really strange. Why should it care what OS is running? 

So I wonder if there's any way to trick Chase.com into letting me connect from Firefox on Ubuntu. I suppose I could install VirtualBox and run the Windows version of Firefox from there, but I'd really rather not. I tried installing the Avant Browser (IE-based) under Wine and connecting from that, but it hangs. And I hate having to boot Vista just to access my Chase account. 

So I wonder if anyone has run into this sort of thing before and found a solution...

---

### Post by ace214 on 2008-09-23
In most cases you can use the User Agent Switcher add-on for Firefox. If the website supports Firefox on Windows, this will generally work. The only time it won't is if the website specifically requires Internet Explorer or Windows Media Player.

Here's a link to the add-on page. [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by tuxxy on 2008-09-23
Media player sites you could always use a virtual machine

---

### Post by Jose Catre-Vandis on 2008-09-24
Install wine, then Firefox for Windows under Wine. (You could install IE if needs be) or try Google Chrome!

---

### Post by nikgare on 2008-09-24
Change banks, and tell them why you are doing so.

---

### Post by zerubbabel on 2008-09-24
The user agent switcher add-on did the trick. Thank you!

---


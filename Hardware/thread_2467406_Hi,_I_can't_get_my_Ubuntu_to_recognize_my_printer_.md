---
title: "Hi, I can't get my Ubuntu to recognize my printer 4 in 1."
date: 2021-09-25
forum: Hardware
---

### Post by aexistenax on 2021-09-25
Hello, I've bought a Canon TS3100 printer 4 in 1, and £I can't find any drivers nor anyway to make it work under Ubuntu.
Could somebody please help me out?
I'm SICK of having to switch to damned Windows each time I've to print a document I made over LibreOffice (or to scan one for that matter).
Thanks in advance for your help and support and patience with a newbie!

---

### Post by fyfe54 on 2021-09-26
Google found this. Hope it helps.

  [https://easylinuxtipsproject.blogspot.com/p/canon-printers.html](https://easylinuxtipsproject.blogspot.com/p/canon-printers.html).

---

### Post by aexistenax on 2021-09-27
Thanks!!!
The printer works flawlessly!!!
But my scanner isn't recognized. :-( 
When I launch [COLOR=blue]scangearmp2 from the terminal it shows an error message that says as follows: <Gtk-Message: 11:41:52.197: Failed to load module "appmenu-gtk-module">


[/COLOR]

---

### Post by brian_p on 2021-09-27
Your scanner is supported by **sane-airscan**. You will also need **ipp-usb** for a USB connection.

[https://github.com/alexpevzner/sane-airscan](https://github.com/alexpevzner/sane-airscan)
[https://download.opensuse.org/repositories/home:/pzz/](https://download.opensuse.org/repositories/home:/pzz/)

---

### Post by aexistenax on 2021-09-27
WOW!!!
:guitar:
Everything WORKS!!Thanks to the Linux Community for your time, help and patience.
Long live Open Source!

---


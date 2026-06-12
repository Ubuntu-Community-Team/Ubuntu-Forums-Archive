---
title: "My session suddenly terminates without warning"
date: 2008-08-20
forum: General Help
---

### Post by harmck on 2008-08-20
Hi All,

I'm not sure if this question has been raised before, I have tried searching for it, but as I can't seem to accurately describe the problem in a few keywords for a search engine. 

When I am logged in sometimes my session is terminated suddenly and a kernel screen is displayed where one of the last messages displayed is 'Checking boot scripts (/etc/rc.local)... [OK]' and immediately after the login window appears again. So its as if something I'm doing triggers the session to be terminated (apart from the obvious logging out scenario..haha). 

If anyone has experienced this and could perhaps help me, or at least point me in the right direction to another thread I would be very grateful. I'd like to find out why this might be happening, I have been using Ubuntu Hardy since its release on my desktop and laptop and it happens infrequently enough that its not really annoying, but it has happened twice tonight. 

Thanks in advance, 

Harry

---

### Post by spiderbatdad on 2008-08-20
Perhaps some specs regarding your computer model would help, and maybe dmesg. ```
dmesg > ~/Desktop/dmesg.txt
```Right click the file that command writes to your desktop, and select "create an archive." Upload the archived file here with the manage attachment tool below.

Also try a google search like: ubuntu hardy heron session crashes...or launchpad hardy heron session crashes.  Include your computer model in the search, even.

---

### Post by harmck on 2008-08-20
Hi, 

Well as it has happened me on 2 completely separate machines the specs of which was different I was kinda hoping it wouldn't be hardware specific. 

My laptop is a Dell XPS M1530 Core Duo 2.5GHz with 4GB RAM, a 320GB HDD. 

My desktop is also a Dell, a Dimension 8300 2.8GHz P4, 512MB RAM, 120GB HDD. 

Attached is the demsg file. 

Regards, 

Harry

---

### Post by spiderbatdad on 2008-08-20
I was wondering if the kernel option for your touchpad would work better in the kopt line of menu.lst...and if that had something to do with logging you out...like ctrl-alt-del, but you say it also happens on your desktop model...hmmm.
I'm loving Intrepid, of course it is still in alpha, and updates are regular and abundant, but so far running great and has all the functionality I need, even gyachi installed without a hitch, so I have video im. I know thats off topic, but, unfortunately, hardy was buggy for me, and I didn't want to go back to gutsy...yay intrepid! Many systems run hardy fantastically; just not mine.

---

### Post by harmck on 2008-08-21
Hey, thanks. 

Hmmm... would consider upgrading to Intrepid... but I'm not sure I'd know enough to fix problems which may crop up. Like yourself I don't want to have to go back to Gutsy. 

Thanks for the tip re: the Touchpad problem, I added it to the default kernel options and to the latest kernel as well. I know it wasn't exactly mentioned in other threads to do this. I'll sort that out later. 

The floor is still open for anyone else who may have had this happen to them before and would have a solution, or even an explanation. 

Rgds, 

Har

---

### Post by amitkher on 2008-08-21
Unless xorg is totally surprised by the failure, you might get some information from the file ~/.xsession-errors. Look at this file, and upload it here as an attachment.

---

### Post by harmck on 2008-08-21
Thanks for that Amitkher, here is part of my xsession-errors file, I think this may have related to the fact I had Google Gadgets running, I just clicked on a link in an RSS feed and the same thing happened again. 

Set options in RNot a regular file: /usr/share/google-gadgets/rss
Not a regular file: /
kbuildsycoca running...
SideBarGtkHost: Load gadget /usr/share/google-gadgets/rss, with option gadget-1, succeeded
Not a regular file: /
/home/harry/.google/gadgets/downloaded_gadgets/81423BB0-2922-11DB-A98B-0800200C9A66.gg/strings.xml:5: parser error : Input is not proper UTF-8, indicate encoding !
Bytes: 0xA9 0x20 0x32 0x30
© 2006 Beatrix Gottanka
^
I/O warning : failed to load external entity "/home/harry/.compiz/session/default0"
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
load.js:73: Old JScript grammar: options("city") =... Converted to putValue()
load.js:74: Old JScript grammar: options("lat") =... Converted to putValue()
load.js:75: Old JScript grammar: options("lon") =... Converted to putValue()
load.js:76: Old JScript grammar: options("sunrise") =... Converted to putValue()
load.js:77: Old JScript grammar: options("sunset") =... Converted to putValue()
load.js:78: Old JScript grammar: options("zone") =... Converted to putValue()
load.js:127: Old JScript grammar: options("city_id") =... Converted to putValue()
main.js:1: Old JScript grammar: options.DefaultValue("lat") =... Converted to putDefaultValue()
main.js:2: Old JScript grammar: options.DefaultValue("lon") =... Converted to putDefaultValue()
main.js:3: Old JScript grammar: options.DefaultValue("sunrise") =... Converted to putDefaultValue()
main.js:4: Old JScript grammar: options.DefaultValue("sunset") =... Converted to putDefaultValue()
main.js:5: Old JScript grammar: options.DefaultValue("zone") =... Converted to putDefaultValue()
main.js:6: Old JScript grammar: options.DefaultValue("city") =... Converted to putDefaultValue()
main.js:7: Old JScript grammar: options.DefaultValue("city_id") =... Converted to putDefaultValue()
main.js:8: Old JScript grammar: options.DefaultValue("zoom") =... Converted to putDefaultValue()
main.js:9: Old JScript grammar: options.DefaultValue("transparency") =... Converted to putDefaultValue()
main.js:10: Old JScript grammar: options.DefaultValue("shift_speed") =... Converted to putDefaultValue()
main.js:11: Old JScript grammar: options.DefaultValue("show_info") =... Converted to putDefaultValue()
SideBarGtkHost: Load gadget /home/harry/.google/gadgets/downloaded_gadgets/81423BB0-2922-11DB-A98B-0800200C9A66.gg, with option gadget-2, succeeded
No slot registered to handle this reply.
No slot registered to handle this reply.

I'm not sure what exactly the issue is, but does any of the above look like it vaguely might throw an exception that would cause a crash like that?

I've safely removed Google Gadgets now. 

Cheers for both of ye're help. Feel free to investigate if you'd like and see if you can re-create the issue. Or perhaps I have something running that is conflicting with it. It doesn't seem to do much harm, apart from wiping unsaved files, which sadly I just lost a site design I was working on :( gutted. 

Harry

---


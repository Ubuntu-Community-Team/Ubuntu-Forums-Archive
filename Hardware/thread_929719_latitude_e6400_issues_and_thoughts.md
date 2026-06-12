---
title: "latitude e6400 issues and thoughts"
date: 2008-09-25
forum: Hardware
---

### Post by shrndegruv on 2008-09-25
Hi all

I have a new latitude e6400, nvidia (quadro 170M I think) graphics.  Ubuntu installed just fine (encrypted lvm yeah), with the following caveats for which I seek help 

1)  suspend to ram: it suspends, but then wakes up immediately.  I had an e6400 with intel graphics (which i returned) and it suspended without issue, so I think it is an nvidia problem.  hibernate works great.  

2)  touchpad: works, but scrolling doesn't.

3)  The cpu is always operating at max speed, even unplugged.  I would expect it to scale down when idling.  

Other than that, this is a great machine.  with compiz (restricted drivers and some tweaks) enabled at idle i have 1-2% cpu usage.  Watching flash has no tearing either (none that i have noticed; certainly not as bad as intel)--I am using the flash 10 beta.  with pandora running (flash music web app) and writing in open office my cpu usage is 20-30%.  The backlit keyboard is awesome.  

My only real complaint is the screen.  I have the LED screen, and the good viewing angle is very narrow.  I much prefer the screen on the inspiron m1530.

The only other thing to be aware of is that the harddrive (I have  the 7200 rpm, 160 GB version) has the load cycle issue (cycles increase really fast).

---

### Post by Lars Noodén on 2008-09-29
The first problem I'm noticing is the video will not go beyond 800x600.

---

### Post by shrndegruv on 2008-09-29
you need to use the restricted nvidia drivers.  My install process was 

install
complete update

I cant remember if it automatically used the restricted drivers or if i had to set it, but if you are having resolution problems Id start there....

another thing I am noticing is that my disk is LOUD.  Everytime the disk light turns on there is a corresponding noise that I don't like too much.  This is wierd because the first e6400 i got, with the same drive specs (160GB at 7200rpm) didn't make this much noise....

edit -- i also learned that the problem with the cpu always running at max speed is a bug in gkrellms cpu freq monitor.  when i use the gnome monitor it is showing scaling all the way down to 800mhz.  powertop reports that it is running at 800mhz most of the time too....

---

### Post by entner on 2008-10-23
I have Intrepid Release Candidate running and all 3 problems you reportet do not exist on my system:

1. Suspend works -> I have the Intel graphics
2. Scrolling works with touchpad, but only vertically. You mean the bars at the right border of the pad?
3. CPU scaling works nicely as shown on Gnome panel applet.

Also the resolution was set correctly to 1440x900.

[Here is my German installation report.]("http://www.entner.net/blog/dell-latitude-e6400-mit-ubuntu-intrepid-ibex-810")

Regards,
Burt

---

### Post by shrndegruv on 2008-10-23
suspend worked with hardy with intel graphics.  it does not work with nvidia (the machine suspends then wakes up immediately).  I think it is an nvidia issue.


powerscaling worked with hardy; its a bug in gkrellms cpu freq monitor.  the gnome applet for cpu freq shows the freqs.


glad to hear that scrolling works (yes the right region of the touchpad to scroll down on a page).  this doesnt really bother me because i use the keyboard to pg down in firefox and whatnot.

---


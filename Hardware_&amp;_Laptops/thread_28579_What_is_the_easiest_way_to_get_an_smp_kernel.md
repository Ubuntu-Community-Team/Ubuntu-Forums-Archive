---
title: "What is the easiest way to get an smp kernel?"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by Tru on 2005-04-20
I am running a dual amd athlon 1800 desktop. When I use fedora core when I install I can just tell it linux smp and it then installs the smp kernel. Is there a way to do this during install? If not then without having to compile a kernel can I do this with apt? If I can do this with apt do I then have to edit any files to get it to show up as an option to boot into or anything else to make it work? or will apt take care of this on the install? 

Thank you for any advice you can give me on this  :)

---

### Post by diebels on 2005-04-20
"sudo apt-get install linux-image-686-smp" and apt takes care of everyting.

---

### Post by gomadtroll on 2005-04-20
You can use one of the package managers, dselect, aptitude,synaptic, there are more, and search for 'kernel-image'  > select the one that has K7 (athlon) & smp in the name. You can use apt-get if you know the name of the package. You can find the name ... search  using  'apt-cache search kernel-image'
greg

---

### Post by Tru on 2005-04-21
Thank you, that worked well I did the apt-get. I am having one last problem. Last night I installed Kubuntu and it set my 19in montior up at 1280x1024 which was perfect I installed Ubuntu tonight and all I get is 640x480 I tried editing the xorg.config file but it will not change it when i reboot. If anyone knows how to fix this please help as I would love to use this distro, but not at 640x480.

Thank You,
Andrew

---

### Post by diebels on 2005-04-21
experimenting with X config is best done by going to a console: CTRL+ALT+F1, become root: "sudo -s", and stopping the display manager "/etc/init.d/gdm stop". Edit /etc/X11/xorg.conf with vi nano or whatever, and start the display manager again: "/etc/init.d/gdm start". You can also see if "dpkg-reconfigure xserver-xorg" can fix the config for you. Knowing something about your video card can be helpful.

---

### Post by Tru on 2005-04-21
Yeah, I got it :) works great now. I have been using fedora core since 1 and I am liking it alot. I really love apt with synaptic.

---

### Post by havesometea on 2005-04-22
I have a similar problem but I am using dual PII-400's.  Would I change the command to reflect i386 or what?

On edit...

NM I found the answer...

---


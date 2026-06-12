---
title: "ATI Mobility RADEON M6-P in Ubuntu"
date: 2010-01-19
forum: Hardware
---

### Post by mo7ard on 2010-01-19
Hi,

I've got a Toshiba Satellite 1900-305 laptop. This computer uses a ATI Mobility RADEON M6-P video adapter.

The only versions of Ubuntu I've used so far, the 9.04 and now the 9.10... both don't use any proprietary driver to accelerate properly my video system. But in 9.04 I really did'n care a lot...

But ever since I installed the new 9.10, my desktop runs with more problems. You know that popup ballon that appears with information on the right top of the screen (usually)? Well... I can't read a single word... it's like a black ballon with some dots in it :(

[IMG]http://img508.imageshack.us/img508/8163/ubuntumo7ard.png[/IMG]

... what could this be?

Using Microsoft Office 2003, I've got the same problem with the font in the default Powerpoint project...

[IMG]http://img300.imageshack.us/img300/8693/powerpoint.png[/IMG]

... can anyone help me, please? This is starting to really p*ss*n me off... I don't have 3D acceleration because it uses a generic driver, and now this... :( help...!

Thank you all!!!!! :D

---

### Post by mo7ard on 2010-01-20
... searching for some sort of solution for my problem, I found a couple of Threads in different forums with some possible answers but... and now the weird part... they edit xorg.conf file... where is mine?? :confused:

I've searched the entire ubuntu system and... no xorg.conf file to edit. I even found a reply about a trick to create a xorg.conf file:

sudo dpkg-reconfigure -phigh xserver-xorg
well... strangelly my gnome works just fine, apart of the issues I told you... HELP!! :(

Thanks a lot! ;)

---

### Post by pi/roman on 2010-01-20
You can create a xorg.conf.new with:
sudo Xorg :1 -configure

which will put it in your /home/*username*/ folder.
Then move it to your /etc/X11/ folder and rename it to xorg.conf

Then of course edit it to your preference. It will probably be necessary to add some modelines which you can create in a terminal with:
gtf xres yres 60

for example:
gtf 1600 1050 60

then copy the output starting from and including "Modeline" to the end and paste it into your xorg.conf under the monitor section for example:
     Modeline "1600x1050"  139.83  1600 1704 1872 2144  1050 1051 1054 1087  -HSync +Vsync

then copy the numbers in the quotes and place them in the xorg.conf screen section next to Modes for example:
    Modes "1600x1050"

---


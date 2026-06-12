---
title: "How do I set-up a DVB-T card ?"
date: 2005-09-10
forum: Hardware &amp; Laptops
---

### Post by Kjell on 2005-09-10
I've been trying to view tv with my DVB-T card for some time. 
I've tried many different viewer-programs without success.

I dont understand how to search chanels, and how view a chanel using a particular 
tv-viewer-program.

Could anyone plaese guide me the basics how to view tv using a dvb-t card.
What do I need to do to get it working. 

What program is recomend, do I need other scaning/tuning  programs  ?

I've run:   

dmesg | grep card

resulting in: 

isapnp: Scanning for PnP cards...
bttv: Bt8xx card found (0).
bttv0: detected: AVermedia DVB-T 771 [card=123], PCI subsystem ID is 1461:0771
bttv0: using: AVerMedia AVerTV DVB-T 771 [card=123,autodetected]

Thanks

---

### Post by Harleen on 2005-09-10
My card worked perfectly without me having to configuring anything. I just started kaffeine, clicked on the DVB-tab and let it scan for programs - nothing more.
Is your card really correctly working? I thought, the bttv-driver was for analogue TV-cards. Is the dvb_core kernel module loaded on your system?

$ sudo lsmod | grep dvb
dvb_core               82920  3 skystar2

---

### Post by Kjell on 2005-09-10
Thanks for your reply

My Kaffeine appears not to have have any DVB button, maybe because  the dvb_core kernel module is not loaded ! 

I tried as root

$ sudo lsmod | grep dvb

nothing happens 

If the dvb_core is missing, how do I load it ?

---

### Post by Harleen on 2005-09-10
This module should be loaded automatically by your TV-card module  (skystar2 for my TechiSat card). But you can try to load it manualy with

sudo modprobe dvb_core

---

### Post by Kjell on 2005-09-10
Yes, I loaded 

$ sudo modprobe dvb_core

Now I get 

$ lsmod | grep dvb
dvb_core               82920  0

I'll try with this to see what happens now !

---

### Post by Kjell on 2005-09-10
No luck, 

Still does no work.

---

### Post by tonym on 2005-09-27
I've recently got my Nebula DigiTV card working with Kaffeine.  I think it has some similarities to your card.  I attach some info taken from the Kernel documentation.

You need a fairly recent kernel - I'm using 2.6.12.

You need to load modules listed in the documentation.  However you may only need to load bttv and dvb-bt8xx,  the rest seem to be dependencies that will load automatically.  bttv may load automatically so you may have to load only dvb-bt8xx.  Check with lsmod.

You may need to load firmware - see the documentation attached.  This isn't necessary for the Nebula card.

Then load kaffeine.  If the above has worked you should have a dvb menu and a dvb tab.  Select channels on the dvb menu and you should be able to tune your card and get a list of channels.

Go to the dvb tab and you should see the list of channels.  They may be greyed out and not selectable.  If so,  look in the menus.  There is an optoin to choose display method between "kaffeine" and "kaffeine gstreamer".  Choose "kaffeine".  You should then be able to select a channel and view it.

Regards

Tony.

---

### Post by jacknel on 2005-10-30
ok fixed it (hopefully its perm)

I typed in this order (not sure if it matterd)

modprob -v dvb_core
modprob -v dvb-bt8xxx




>  any more help, i had this working then all of a sudden, it reverted back to no DVB tab and a greyed out version of the DVB icon

i have 

modprob dvb-bt8xxx
modprob bttv
modprob dvb_core

already :(



---

### Post by Kjell on 2005-11-27
Now my Avermedai DVB-T card is upp & running, its great.

I like to share how I managed to get it working, but beeing a newbie and follwing a couple of leeds on this and other forums - I cant say how its done exacly, but only share the information I used to get it to work.

As follows:

I'm using Brezzy Badger, the system reconized that the Avermedia card was installed, but still not working as it did not have a so called "frontend" alocated to it. 

I did find a excellent How To get the Avermedia card to work with Ubuntu 5.05, at: [http://www.pvrguide.no-ip.com/bbs/lofiversion/index.php?t5052.html](http://www.pvrguide.no-ip.com/bbs/lofiversion/index.php?t5052.html)

However I could not start the menuconfig, to get the kernel config menues.
So I used tseliot's excellent  HOWTO: Kernel Compilation for Newbies
[http://ubuntuforums.org/showthread.php?t=85064&highlight=vanilla](http://ubuntuforums.org/showthread.php?t=85064&highlight=vanilla)

Once I could get the kernel config menues, I did all the settings according to 
[http://www.pvrguide.no-ip.com/bbs/lofiversion/index.php?t5052.html](http://www.pvrguide.no-ip.com/bbs/lofiversion/index.php?t5052.html)

And vola the card was working.

I did start with Kaffeine player, configuring DV-T with the frontend name:
Zarlink MT352 dvb-t and type: dvb-t using the source: se-Stockholm_Nacka
(as it close to my house)

Then I could do a channel seach using Kaffeine

When I tried to use Xine, there was no channels.config file that it could use for the channels, to get this to work I had to use a scan command  to find the channels.

To use the scan command it will need the region, as in my case se-Stockholm_Nacka, I did seach for this file and found it: 
/usr/share/doc/dvb-utils/examples/scan/dvb-t/se-Stockholm_Nacka

using this for the scan command, and outputting it to the file that xine needs 

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/se-Stockholm_Nacka | tee /home/*YourHome*/.xine/channels .conf

And we got TV xine also.

Thanks 
KJell

---

### Post by Kjell on 2005-12-26
Well, well ! Now a new how-to setup guide is available for the old Avermedia DVB-T 771 card availabe at 

[http://www.avermedia.com/docs/pdffiles/linux.txt](http://www.avermedia.com/docs/pdffiles/linux.txt)

//Kjell

---


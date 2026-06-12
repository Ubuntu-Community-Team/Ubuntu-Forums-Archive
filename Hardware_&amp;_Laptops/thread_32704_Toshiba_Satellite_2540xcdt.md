---
title: "Toshiba Satellite 2540xcdt"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by vector on 2005-05-09
Hi all
Warning Newbie
I have linux running on a desktop but cant honestly say I know how it runs ;)

I have loaded ubuntu on a desktop. it worked frist up, its basic, no net , just word pro and basic games (for my mum)

I WANT to load linux onto my toshiba and Id like to use unbuntu. and I d like to use a wireless internet connection. card is a minitar mnw2BPCM (which wouldnt work with the win98 that was on the laptop) cause it needs win98SE. Right thats it im going linux.

I want basic net access and office use so no big deal??

Am I going the right path,, will i get help and a hand to hold ;)

thanks guys

---

### Post by az on 2005-05-09
You should be fine.  Ask any questions you need to ask...

---

### Post by vector on 2005-05-09
is there a particular flavour of ubuntu or do i just grab the latest offering

---

### Post by az on 2005-05-09
Use the Hoary install cd.

---

### Post by dbott67 on 2005-05-09
[QUOTE=vector]Hi all
Warning Newbie
I have linux running on a desktop but cant honestly say I know how it runs ;)

I have loaded ubuntu on a desktop. it worked frist up, its basic, no net , just word pro and basic games (for my mum)

I WANT to load linux onto my toshiba and Id like to use unbuntu. and I d like to use a wireless internet connection. card is a minitar mnw2BPCM (which wouldnt work with the win98 that was on the laptop) cause it needs win98SE. Right thats it im going linux.

I want basic net access and office use so no big deal??

Am I going the right path,, will i get help and a hand to hold ;)

thanks guys[/QUOTE]

Go for it!  I'm running Hoary 5.04 on a Toshiba Tecra 8000.  Read this [thread](http://ubuntuforums.org/showthread.php?t=32651) that covers some of the issues I faced.  It also includes some links to Toshiba's web site for specs and other info useful for putting Linux on Toshiba laptops.

Here's a link to Toshiba [hardware specs](http://linux.toshiba-dme.co.jp/linux/eng/speclist.php3) and a link to the [Satellite 2545 XCDT](http://linux.toshiba-dme.co.jp/linux/eng/spec.php3?model=PAS254U-T6).

With a little patience and some help from the knowledgeable people in this forum, I think you'll be very happy.

-Dave

---

### Post by vector on 2005-05-10
ok ta this is from the laptop so we are getting on ok.
However. the screen res is 640 and system/pref/screenres wont give me any other choices. the screen view is really "bad"

Anyway ill read those posts and site urls and see what i can sort out.
its also verrrrrrryyyyy  slllllooooooooww ;) took quite some time for firefox to come up

---

### Post by az on 2005-05-10
I needed to reconfigure the x server to go down to 15 bit color depth, since my video card does not have a lot of memory.  You laptop may support a higher color depth than 15 bit, but that may be your problem.

Yes, if you only have 64 megs of ram, it will be slow.  You can either add more ram, or you can install a leaner graphical environment like icewm or XFCE4


All this can be done through synaptic.

---

### Post by vector on 2005-05-10
ok screen res is up set to 16 bit, its also a little quicker.
Ok on the more ram . Ill be looking at this and a new battery ;( if all this keeps going well

now the only problem is sound.
I did as dbot67 suggested. and followed the thread.
but on restart it beeps alot and says it cant find the Yamaha opl3-sa soundcard.
i looked  closer at your thread and noticed two things
first you have opl2-sa2 while the satalite page indicates i have a opl3-sa3
I changed this line to no avail ;(

then I noticed you """3.) sudo gedit /etc/modprobe.d/tecra_sound"""
of course mines not a tecra so im not sure what to mod

i noticed that """"sudo apt-get install libesd-alsa0"""
also had some worries as it had to remove libesd0 and said lots of things needed it however it kept going and seemed to install without real errors

so i looked and did this """sudo gedit /etc/asound.conf"""
according to the thread
it was empty so i filled it as per thread instructions.

but on alsa restart got all those beeps and this reacurring

 Invalid card number.
Usage: amixer <options> command
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
Available commands:
  scontrols       show all mixer simple controls
  scontents       show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> command
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
Available commands:
  scontrols       show all mixer simple controls
  scontents       show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control                   [ ok ]


just so you know i cut n pasted the text in the threads so I dont suspect typos.

any ideas

---

### Post by mrbaz on 2005-07-14
[QUOTE=vector]
but on alsa restart got all those beeps and this reacurring

 Invalid card number.
Usage: amixer <options> command
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
Available commands:
  scontrols       show all mixer simple controls
  scontents       show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> command
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
Available commands:
  scontrols       show all mixer simple controls
  scontents       show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control                   [ ok ]


just so you know i cut n pasted the text in the threads so I dont suspect typos.

any ideas[/QUOTE]

This EXACT same thing happens to me.  WTF do we do?

---

### Post by vector on 2005-08-23
> this EXACT same thing happens to me. WTF do we do?
i have no idea. i check back ocasionaly to see if anyone has any ideas. but still no sound.
the problem now is that i have twiddled so many things there is a good chance even if it did work I wouldnt know it :( ](*,)

---


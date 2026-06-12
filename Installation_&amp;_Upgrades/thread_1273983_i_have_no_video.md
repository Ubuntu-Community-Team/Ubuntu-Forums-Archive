---
title: "i have no video"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by milinko on 2009-09-24
sorry forgot to add to the title its jaunty im having trouble with
system specs
cpu: intell core 2 quad 2.33ghz 4mb cache (12 all together) x64
motherboard: asus p5q
graphics card: ati radeon 4770 512mb with a vga monitor and and a HDTV via hdmi
ram: 8Gb ddr2
hard drives: 2 western digital 640gb 390gb free on install disk
soundcard: onbord realtek hd audio
current os: windows vista home premium x64

what happens is i install useing a disk i made from the iso image with ultraiso install no errors install completes successfully then askes for reboot then when i select ubuntu it loads and after i get past the loading logo after it has stoped continuasly going by and then fill the bar the logo goes away and then the screen goes blank and my monitor goes into standby and my tv get no signal from my computer when i hit a few buttons (like enter a few time them esc a few time) my HD lite flashes a bit like it would if i were doing the same thing on windows so i know the install worked i just get no video i downloaded the x64 version since my cpu is a x64 architecture.
is my computer compatible?
am i missing something?

---

### Post by etnlIcarus on 2009-09-24
Try unplugging either your monitor or the HDTV, then booting up. Failing that, keep one or the other unplugged, then reinstall. If you're able to install and reboot successfully with one monitor, then look into adding the second one after.

I never had much luck with multi-monitor with my Radeon 9550 and I found that having multiple monitors connected would often confuse auto-detection and initial configuration.

---

### Post by milinko on 2009-09-24
thx ill try that rite now and see if it works

---

### Post by rreese6 on 2009-09-24
In your grub menu select to boot in recovery mode
you will come to a superuser prompt(#)
type this```
:

Startx
```

it should fail, if you get a black screen try CTRL+ALT+Backspace
when at the prompt type: ```

dmesg | tail -n20
```

that should give you some insight to why your video card is not working.
 what would be more helpful is to do this:```

dmesg |tail -n20 >> report.txt
```
type "ls" to see report.tx is written.
then go to /mnt or /media and find your windows drive ( I assume it is your fist partition) 
cd /media/windows
ls to find a place to copy the report file.
then cp /root/report.txt . (there is a space and period(dot) at the end) that will copy the report to your windows partition.

reboot into windows, and post the contents of the report.txt file here.

---

### Post by milinko on 2009-09-24
awsome thx entl it worked im useing it rite now hehe now can the res go any higher than 800x600? or do i need to w8 for the updates? OR download my vid card drivers again?

---

### Post by etnlIcarus on 2009-09-24
Download your card's drivers again.

I'd wait until *after* installing the drivers and restarting, before I'd even consider re-connecting the HDTV.

---

### Post by milinko on 2009-09-24
huh well i downed the newest drivers for my card but they wont run it says its a .run file im going to try useing the disk maby that will work then i can just update but the .run say something about some code or sumin idk any clue?

---

### Post by etnlIcarus on 2009-09-24
Use the drivers in the repos before trying the latest drivers from AMD. There's an application somewhere in the settings/system menu called either jockey-gtk or "restriced something manager". Use that to install your video drivers.

---

### Post by milinko on 2009-09-24
](*,)well i found the program in system dont mem what it was and i got the same issue no vid but apparent signs of activity when i blindly logged in so i restarted and ran the graphics fixer in the recovery thingy and now it loads like b4 then i get some pretty green bar pixleization with red block at the very top and it has a 2 small like 1/2 sized pixleized ubunto logo like the loading one and then the system freezes now im back to windows(DAM YOU BILL GATES lol) so well...now what?](*,)

---

### Post by etnlIcarus on 2009-09-24
Looks like you need to download and build the latest proprietary ATI driver, then.

Start up Ubuntu, then once it's reached the login-screen, press Alt + F2. You'll be presented with a text login screen. Login, then run:

```
sudo aptitude purge xorg-driver-fglrx fglrx-kernel-source fglrx-amdcccle
```
Then:
```
 sudo shutdown -r now
```
Once you restart, you should be back to your 800x600 desktop.

Now, to install the latest drivers. I'm a bit rusty here so if anyone's got a walkthrough, it would help.

First, you need to get all the bits and pieces needed to build the drivers:
```
sudo aptitude install linux-headers-generic build-essential debhelper
```
I might be missing a couple of things, here but I guess we'll find out soon enough.

Next, [the installation instructions you want start on page 10](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat98-inst.pdf). We're going to build the, "Distribution specific", driver packages.

By 'superuser', it means placing *sudo* before any commands you run. So, for instance, if you put the .run file on your desktop, you'll want to do the following:
```
sudo ./Desktop/ati-driver-installer*.run
```

Follow the instructions in the pdf, starting from page 10, and tell me what happens.

---

### Post by etnlIcarus on 2009-09-24
Oh and before doing the aticonfig --intial stage of the instructions (provided you get that far), you'll want to do a:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bkp
```
In case the new drivers break again. That way, if things go awry, you can alt + F2 again, login, and perform the above command backwards (copying the backup over-top of the original).

---

### Post by milinko on 2009-09-24
ok ill try that this time im going to put ubuntu on my other drive aswell that way i can also partion it and my windows and ubuntu drive have the same amount of storage aswell:guitar:i just had to do it he looks so cool:guitar:
             HA electric and rythem hehe

---

### Post by milinko on 2009-09-24
ARG ok now ubuntu was freezing after it loaded so i couldent log in so i reinstalled it and well i have no idea what im doing here i cant start the file i dont know what im doing here im trying to follow the install instructions from the pdf but i can even get it to open(the driver installer not the pdf) i need very specific instructions my username is xander(if it helps) ive tried all the thing i could think of the driver name is ati-driver-installer-9-9-x86.x86_64.run and its on my desktop i looked for instrucions for 9.9 but theres only 9.8 instructions hope all of this helps if there anything else u need to know tell me

---

### Post by etnlIcarus on 2009-09-24
In the folder you downloaded the .run file to, right click an empty space and choose, "open terminal here", or something to that effect. Then simply type:
```
sudo ./ati-driver-installer*.run
```

Also, you need to tell me where you got up to in my instructions: did you get as far as installing build-essential, debhelpers, etc?

Anyway, I'm afraid I'll probably be AWOL for the next few hours. Hopefully someone else can guide you through this.

---

### Post by milinko on 2009-09-24
yea thats as far as i got that was the only thing i could get to work

---

### Post by etnlIcarus on 2009-09-24
Ahh, think I figured out my mistake: [from this thread](http://ubuntuforums.org/showthread.php?t=1273767).

Right-click the .run file, go to properties and somewhere in the properties dialogue (if there's a Permissions tab, it'll be in there), there's an option to 'allow executing this file as a programme'.

Then, open a terminal in the .run file's folder and retry either:
```
sudo ./ati-driver-installer*.run

or

sudo sh ati-driver-installer*.run
```

---


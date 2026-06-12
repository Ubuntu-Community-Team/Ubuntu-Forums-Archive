---
title: "Install Ubuntu on Microclient Jr. ?"
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by sbutton on 2007-02-26
Hi,

I'm considering installing Ubuntu on a Microclient Jr. from Norhtec [http://www.norhtec.com/products/mcjr/index.html](http://www.norhtec.com/products/mcjr/index.html) which seems like a very reasonably priced solution. (USD $120)  I want to replace the old fujitsu PIII 400 MHz PC that I have which is noisy and probably uses too much power (and doesn't work all that well).

Will it work? 

Will it be faster / slower? (The Microclient is only 200 MHz, will it be slower than the PIII 400 MHz - if that isn't a stupid question)

Can I get away with loading Ubuntu onto a CF card (4 Gbyte for GBP £45)?

Any other thoughts? 

Thanks,

Steve

---

### Post by samichx on 2007-05-21
The Microclient Jr. is very limited on resources, and I wouldn't suggest Ubuntu directly. DSL and Slax variants using IceWM seem to operate - it is the bulky (feature rich?) Gnome that drags it down. XFCE is a bit iffy still when packages with all of the extras.

Forget multitasking - it will operate at its best doing ONE thing at a time. Making it an excellent PC for Kids. Access online games, setup non-3D games from Ubuntu repos (Wesnoth runs, and it is good to play online with others). We even have a couple emulators set-up which when connected to a standard TV with VGA inputs makes it as good 1994.

Buy it if you want - just expect a little work optimizing it and cutting back unnecessary extras.
If you convince you boss to buy a bulk order for the company (or campus) throw in a couple for your buddies, at this price it's like buying (2) sweaters.

---

### Post by honeydew on 2008-02-15
I just attempted to install dapper drake lts to 2 microclients and right afterboot it fails and restarts the machine.. It gives no errors even with the quiet flag turned off.  I am attempting to try debian etch now.

---

### Post by nicolas314 on 2008-02-21
Ubuntu is probably too heavy to run on a MicroClient Jr, though as mentioned above it could theoretically run a basic desktop for children. I installed Debian and do not regret it since, it makes a great programmable network appliance! Think NSLU2 with a lot more power.

You may want to check out the following page:
[http://nicolas314.wordpress.com/norhtec-microclient-jr/](http://nicolas314.wordpress.com/norhtec-microclient-jr/)

---

### Post by honeydew on 2008-02-21
mm.. debian etch installed with out hitch.    More then enough power for my needs.

---

### Post by puleen on 2008-03-16
Did you follow a tutorial on installing etch on MicroClient Jr? If so, could you share that?

Thanks,

---

### Post by honeydew on 2008-03-18
Nope I installed as per the default instructions.  We are using these things in a project and I may be making a etch image that could be copied to a disk, as to avoid installation.  If/When we get around to this I will post links to the images.

---

### Post by puleen on 2008-03-18
If you are able to create an image that can easily be copied to a CF card or what not and make that available, it would be great. I have had nothing but trouble and so far the only linux that I have been able to get working is Puppy. However; I would like to get etch working and possibly setup a web server to use the Junior as a demo machine of sorts.

Cheers!

---

### Post by honeydew on 2008-03-19
strange.. I wonder if hardware is different in some batches.. what happened when you tried to install etch?

---

### Post by puleen on 2008-03-20
I am not sure if the hardware would be different, but it is a possibility.

In my case after I tried three different installs, very slim install of Ubuntu with a light weight x window system, and etch. I carried this out using the qemu method as well as the penlinuxdrive.com methods and in both cases, the system would boot up and get to the CF card but then nothing would happen.....the cursor would just blink, nothing would get loaded. I tried many a times to make sure that the  MBR was getting written to the CF. I event tried installing etch and ubuntu (lightweight) on to a 2GB USB memory key and trying to boot that up through the Junior, but without any luck.

Cheers!

---

### Post by honeydew on 2008-03-20
oh.. hrmm.. I used a usb cd-rom to install etch..   I didnt have good luck with ubuntu.  Im looking around for a extra cf flash that I can reproduce the install on(I know I have one around here some where......) once I spot one Ill up a image...

---

### Post by josh_marshall on 2008-03-20
For what its worth, I also had this issue. No matter what I tried, Debian Etch, Ubuntu, Xubuntu, etc. it would perform in the exact manner as described.

---

### Post by puleen on 2008-03-21
honeydew, I was thinking of getting a USB CDROM drive and using that, but apart from installing on micro client jr the usb cddrive would have no other use and hence be wasteful in my opinion.

If you could image it up, in your free time, I would really appreciate it. In the mean time I will try to play around with installing other distro's and see how far I can get with it :)

Cheers!

---

### Post by |nferno on 2008-03-23
I have been able to install Debian etch via a net install iso on a pen drive however on all three times it didn't detect my nic this is rather annoying as i now have to fiddle around compiling kernels. i haven't found anybody else with this problem.

---

### Post by honeydew on 2008-03-26
grr.. tried uploading the image to my server last night.. and it conked out about halfway through.. scp really neads a resume feature =/... hrmm maybe rsync will do the trick =]....  Ill post once its up.

---

### Post by honeydew on 2008-03-26
mmm rsync did the trick.. here is a page with the image and a quick method of installation

[http://wiki.arcintel.com/doku.php?id=microclient_jr](http://wiki.arcintel.com/doku.php?id=microclient_jr)

---

### Post by puleen on 2008-05-25
Can't seem to load that site. Are you able to get to it?

---

### Post by honeydew on 2008-05-26
arg.. bad news at the momment.. I moved recently and I lost the harddrive with the image on it..  it was not that hard todo so when I get a bit of time and some bandwidth Ill put it back online.

---

### Post by puleen on 2008-05-26
honeydew, believe it or not I finally got debian installed last night and set it up with the LAMP stack. The only worry that I have now is to somehow remove all non-necessary crap that was installed and also if there was somehow a way to avoid having to do too many write to the CF card. Since, CF cards do have a write capacity.

So far it is looking good, I didn't realize that Postgres is installed by default, but I will have to install mysql on there and set it up as a miniscule web appliance of sorts.

So far so good, it was a joy to finally get the damn thing working.

One question, I have wireless on the Micro Jr. Do you know if wifi connection can be configured in a headless configuration? I didn't install the Desktop Environment on it, since there's no point to running it as a desktop.

Cheers!

---

### Post by honeydew on 2008-05-28
yah wifi is configured via iwconfig..   if you dont see the wireless card you may need to install the restricted module kernels.. Im not sure how to restrict the writes for debian off the top of my head..

---


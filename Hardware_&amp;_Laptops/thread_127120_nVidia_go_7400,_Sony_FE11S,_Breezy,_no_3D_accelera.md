---
title: "nVidia go 7400, Sony FE11S, Breezy, no 3D acceleration"
date: 2006-02-08
forum: Hardware &amp; Laptops
---

### Post by theBuggane on 2006-02-08
I have a new Sony FE11S laptop, which is excellent. I have a 40GB partion where I have installed Breezy (dual boot via Grub, the rest of the space taken up by Windows).

The install was smooth and I have a machine I can use. However, I do not appear to have 3D acceleration (though the GL screensavers work slowly). 

I cannot install the nVidia drivers for the go7400 card, neither via the package manager nor using the install binary from nVidia. Both methods (see [this]("http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+install")) report success, but the GDM does not start afterwards...

I can recover by restoring my /etc/X11/xorg.cong and the key line that causes the problem is the change of the driver line from "nv" to "nvidia".

Has anyone had success with a nVidia go7n00 card?

---

### Post by duke42 on 2006-02-12
I have the same problem, but on a FE11M.
[LIST]
[*] 7667 (the latest in breezy) doesn't recognize the chipset
[*] 8178 (the latest from NVIDIA) doesn't get the modeline settings correctly.  It says that width 1280 is too large for the display.  I don't know if this is only cause, but the display stays black.  I can switch to a console and everything works there, but not the X11 display.
[*] the nv driver gives display errors after some time and the only remedy is to logout and login again.
[/LIST]

So, I don't know what to do.

bye, duke42.

---

### Post by duke42 on 2006-02-14
I just see, that the chip isn't supported by the NVIDIA driver:

[http://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-a.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-a.html)

Hmm well&#8230; but it gets detected, this I can say.

cu, duke42.

---

### Post by Blashyrk on 2006-02-14
Hello to everybody!!

I am very interesting in that laptop (to be honest, its little brother FE11H), and i need that linux runs on it. There are VERY LITTLE info about this laptop and linux. i have only found this [http://www.presence-pc.com/tests/portable-sony-vaio-fe11s-427/4/]("http://www.presence-pc.com/tests/portable-sony-vaio-fe11s-427/4/") and it's in French (I'm spanish, so sorry for my english :(  ). Both of you have found problems with the nvidia 7400 graphic adapter. How about the rest of components, have you found any problems? the wireless runs ok? and the cpu, it's really new, Ubuntu Breezy recognizes it well? on the link above, they tried to run Knoppix without success. Any suggestion about buying the vaio FE11H to run ubuntu (or not) will be wellcome. If the only component that causes problem is the graphic, i know that nvidia will support the chip soon or late. (i hope sooner than later :))

Once again I'm terrible sorry for my english :( . And thank you very much!!

---

### Post by Blashyrk on 2006-02-14
My answers to me :D
1.- About the Intel Core Duo... [http://support.intel.com/support/chipsets/sb/CS-022095.htm]("http://support.intel.com/support/chipsets/sb/CS-022095.htm")

2.- About the wireless... [http://support.intel.com/support/notebook/sb/cs-006408.htm]("http://support.intel.com/support/notebook/sb/cs-006408.htm") For this one we will have to wait...> Intel® PRO/Wireless 3945ABG Network Connection
Driver is expected to be available Q1 2006.

But I still want to know your opinions about the laptop, general feelings, and so... 
Thank's a lot again

---

### Post by Blashyrk on 2006-02-14
Me again!! hehehe

Now about the nvidia 7400... [http://www.nvnews.net/vbulletin/showthread.php?t=64594]("http://www.nvnews.net/vbulletin/showthread.php?t=64594") 

A Nvidia member answers... > The next driver release will support the GeForce 7400.

Thanks,
Lonni
Once again, time is the answer...

---

### Post by theBuggane on 2006-02-14
thanks for all the info. grazias!

as for the laptop (FE11S), it is excellent though i have no sound, no wireless and no 3d acceleration. also, the power management is not right yet.

the machine is very new so this not unexpected. it is part of the challenge!

still even with these (hopefully temporary) problems, Ubuntu runs well. i'd certainly recommend the laptop, even if it is Windows-biased for the moment...

---

### Post by bullraiser on 2006-02-17
Hi,

I am thinking of buying this Sony laptop FE11S and installing breezy on it. How do you think the response of Breezy on this laptop. 

I would be most probably doing lof of professional work on this laptop like Java development, Photo Editing, Streaming etc., on linux. I have shortlisted Ferrari 4005 (Turion M37), Sony FE11S (Dual Core). 

Will appreciate, if anyone will put some bechmark on this?

Cheers

---

### Post by theBuggane on 2006-02-18
If I was buying the laptop just for Linux, I would buy a better supported one, not the FE11S. Not yet...

However, if Linux is just for general interest and you have a dual boot, it is an excellent machine.

---

### Post by jede on 2006-02-19
Hi,

I have a VAIO FE11M and have bigger problems toget it to work with Ubuntu Breezy. 3D and WLAN is not that important for me right now. 

The biggest problem is that I'm not able to set the screen brightness. I've tried the sonypi module and the spicctrl tool without success.

I've also tried the sony_acpi-0.3 module as described here:
[http://users.skynet.be/thomasvst/linux-on-laptop/](http://users.skynet.be/thomasvst/linux-on-laptop/)
I had also no sucess with it :-(

Was anybody able to set the brightness level of the screen ? The maximum level is making me blind...

I made my tests with the Breezy kernel 2.6.12-10 (smp), and with vanilla kernels 2.6.15.4 and 2.6.16rc4. All have the same problems.

BTW: Sound is also not working, can someone add comments here ?

Bye,
Stefan

---

### Post by bullraiser on 2006-02-20
I am still finding a great deal to go with either Sony VAIO FE11S (Intel Core Duo 1.83 Ghz) or Acer Ferrari 4005 (2.0 Ghz AMD Turion). Since AMD is planning to launch Turion Duo Mobile in the second quarter, I am rethinking on the Ferrari option but though have some few queries on FE11S benchmarks:

1. Is that nVidia go 7400 truly performs the dynamic memory usuage. I was comparing ATI X700 series and as per benchmark results, ATI is surpassing nVidia with the graphics performance. How's the support for LINUX from nVidia and ATI?

2. Hard drive spec is 160 GB 4200 rpm. Doesnt this makes the drive to perform read/write operations slower compared to 5200/7200 rpm? I was thinking 4200 rpm is out of market, but Sony is bringing up new VAIO FE series with this drive... 

3. Memory spec was 1 GB DDR II PC 4200 (2  * 512). I dont think this really boost up the performance as compared to Acer Ferrari 4005 DDR III PC 4700. Is there an option to upgrade to DDR III ?

4. How fast the applications in Linux and Windows load on FE11S? 

5. There was some additional eye-catching camera added by Sony (0.13 megapixel camera). I dont think thats really useful to provide nice conference real time images. Any idea abt this?

Anyways, whatever I've decided to go for either Sony VAIO FE11S or Ferrari 4005, my first action is to dual boot with Breezy and posting to this forum.

Cheers--

---

### Post by paneios on 2006-02-25
I am an owner of Sony FE11S. I have installed Breezy on it and i have the following problems.

1. The Nvidia is not working and it is going to be supported next month
2. Wifi is not working as well and is going to be supported in thw Q1 of 2006
3. No sound. Only PCM device is working. 
4. ACPI is working with 2.6.12 kernel problems with 2.6.10 the laptop os not turning off. Upgrade needed.
5. Camera is not working

Comments. I think this laptop is really cool. It is fast with great screen. I think that when vga, wifi and sound  would work it is going to be a great choice. It is a good invensment for the future. Not recommended for people that change laptop once a year. 
Personally i am working all the time on it, on linux of cource.

---

### Post by paneios on 2006-03-21
Sound is working with alsa:1.0.10
and kernel:2.6.15-19

for wifi
[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

I suggest the owners of this laptop to upgrade immediatelly to Dapper.

---

### Post by Blashyrk on 2006-03-21
> Sound is working with alsa:1.0.10
and kernel:2.6.15-19

for wifi
[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

I suggest the owners of this laptop to upgrade immediatelly to Dapper.

I confirm this. I'm using dapper in FE11H and have just upgrade the kernel to 2.6.15-19 and sound works perfectly (the gdm sound surprised me hehe)

I am going to test the ipw3945 now! I didn't know about that!

PD: I'm really sorry for my bad english, excuse me please :(

---

### Post by Blashyrk on 2006-03-21
Ok the wireless will have to wait, i hope the driver will be out in a few weeks and dapper will support it. I do not need it urgently. 

With the new kernel i have test the hibernate. With the "old" one didn't work. With the new one the process to save the data to the disk aparently works fine ("this is going great!" I thought) But in the wake up process it fails miserably. Has anyone tried it with sucess? The laptop has 1GB of Memory, and my swap partition has the same size (yes, i know, my fault) Can this be the problem?

Thanks to all!

---

### Post by avilella on 2006-03-30
The Dec 2005 drivers from nvidia work with the appropriate modeline:

[http://www.nvnews.net/vbulletin/showthread.php?t=67307](http://www.nvnews.net/vbulletin/showthread.php?t=67307)

Although I couldn't get them to work with xinerama using an extra external LCD...

---

### Post by Blashyrk on 2006-04-05
Hello again!!

Another kernel update has arrived!! 2.6.15-20 and hibernate works!!!! almost perfectly!! Desktop resumes ok, sound ok too, but my usb mouse does not work if it's inserted while resuming. I switch it off, on again and voilà!

A very nice surprise that hibernate the laptop works!! very very very nice surprise!

---

### Post by RiffX on 2006-04-08
Hi,

Just to bring thins together for anyone reading this thread with a FE11S / FE11H running Ubuntu Breezy, I've found the following solutions for sound and wireless...

**SOUND**

Install the following in Synaptic:
[LIST]
[*]build-essential
[*]automake1.9
[*]autoconf
[*]cvs
[/LIST]

Then type the following in Terminal:

```
mkdir alsa

cd alsa

cvs -q -f -z3 -d ":pserver:anonymous:@cvs.sourceforge.net:/cvsroot/alsa" export -D 2006-03-13 alsa-driver

cvs -q -f -z3 -d ":pserver:anonymous:@cvs.sourceforge.net:/cvsroot/alsa" export -D 2006-03-13 alsa-kernel

wget http://librarian.launchpad.net/1728369/vaio-stac7661-test3.diff

patch -p0 <vaio-stac7661-test3.diff

cd alsa-driver

./cvscompile

sudo make install

echo "options snd-hda-intel model=vaio" | sudo tee -a /etc/modprobe.d/snd-hda-intel
```

**WIRELESS**

Install 'make', all gcc compilers, the linux headers and the linux source.

Download latest ieee80211 subsystem from [here]("http://ieee80211.sf.net").

Download latest Intel® PRO/Wireless 3945ABG Driver for Linux from [here]("http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?strState=LIVE&ProductID=2259&DwnldID=10315&agr=Y&lang=eng").

Place both in the same directory (eg, /home/YOURUSERNAME/wireless).

Then type into Terminal:

```
tar xzvf ieee80211-1.1.12.tgz
cd ieee80211-1.1.12
make 
sudo make install
cd ..

tar xzvf ipw3945-linux-1.0.0.tgz
cd intel-ipw3945-1.0.0

tar xzvf ipw3945-1.0.0.tgz
cd ipw3945-1.0.0
make
cd ..

tar xzvf ipw3945-ucode-1.13.tgz 
less ipw3945-ucode-1.13/LICENSE.ipw3945-ucode  <<<END to scroll down, q to quit>>
sudo cp ipw3945-ucode-1.13/ipw3945.ucode /usr/lib/hotplug/firmware/

tar xzvf ipw3945d-1.7.18.tgz
less ipw3945d-1.7.18/LICENSE.ipw3945d  <<<END to scroll down, q to quit>>

sudo cp ipw3945d-1.7.18/x86/ipw3945d /sbin
```

The driver is now installed.

To manually load it, type:

```
cd /home/YOURUSERNAME/wireless/intel-ipw3945-1.0.0/ipw3945-1.0.0
sudo ./load
```

Then configure the wireless connection with the Ubuntu Network Configuration tool.

I haven't figured out yet how to automate the loading, but you can check [this]("http://www.ubuntuforums.org/showthread.php?t=156758") thread for my progress.

I can also confirm that sound works from scratch with Dapper. Haven't tried wifi on Dapper yet.

Good luck!

---

### Post by Blashyrk on 2006-04-10
Hello!!

The new nvidia drivers 87.56 are in dapper repositories. I have installed it and I have 3D Acceleration at last!!! yes!!! (Ole!) 

Greetings!!

---

### Post by chriso on 2006-04-11
Ive just bought an FE11S and am completely new to Linux. I want to do a dual boot as still need to use Winblows for some software, but all of these installation instructions scare me a little.

---

### Post by jede on 2006-04-16
The biggest problem for me was that the screen brightness can't be changed in linux, it's always at maximum. Has somobody solved this problem ?

Bye,
Stefan

---

### Post by roby811 on 2006-04-19
Hi,
i'm an italian boy, i have a [**blog**]("http://1spray.splinder.com/") where i post some news about [**Linux on Sony Vaio FE**]("http://1spray.splinder.com/").
If you have any suggestion, comment, news, contact me!

---

### Post by jede on 2006-04-19
Sorry, I can't unserstand your italian blog.
Are the brightness settings keys are working for you ?

Bye,
Stefan

---

### Post by roby811 on 2006-04-20
No, but if you read this

[http://www.montellug.it/wiki/index.php/Ubuntu_on_vaio#TASTIERA](http://www.montellug.it/wiki/index.php/Ubuntu_on_vaio#TASTIERA)
[http://www.ubuntuforums.org/showpost.php?p=487144&postcount=7](http://www.ubuntuforums.org/showpost.php?p=487144&postcount=7)

you should be able to do it!


Hi!

---

### Post by jede on 2006-04-22
These english instructions seems to be for other models.
So please tell us: does the brightness setting keys are working on your FE11 in Linux ?

Bye,
Stefan

---

### Post by roby811 on 2006-04-26
No.
I tried with ubuntu 6.06 beta, and after the sistem start, the hotkey for brightness don't work (for audio work).
But i have' nt made anything for resolve this, and i think that if you spend a little of time, you should resolve the problem.

Hi

---

### Post by jede on 2006-04-28
Thanks, this answers my question.
This is the same situation I also had. The acpi-stuff has changed a lot in the new FE11 according to the older models were the keys have been working. 
Yes, when people spend their time on find a way it will work sometime.

Thanks,
Stefan

---

### Post by slight on 2006-04-30
there's a fix that's been committed to the kernel for the sonypi acpi stuff on FExxx laptops, so hopefully some bits should start working soon. However I believe there's also an issue with the nvidia drivers and changing the brightness.. haven't seen anyone manage this yet.

---

### Post by roby811 on 2006-05-08
hi,
i have a good news!
the news version of smartdimmer can change the brightness of sony vaio fe11h!!

I have tried also the bluetooth service, and it works! (i used a bluetooth external key, and my sony ericsson t630)

---

### Post by Blashyrk on 2006-05-08
[QUOTE=roby811]hi,
i have a good news!
the news version of smartdimmer can change the brightness of sony vaio fe11h!!

I have tried also the bluetooth service, and it works! (i used a bluetooth external key, and my sony ericsson t630)[/QUOTE]

Very very very good news!! I have tried smartdimmer and works perfectly. I'll try to bind them to F5 and F6 keys. 

And another very good news. With the new kernel 2.6.15-22 the wireless is working!!! (ole, ole, ole). Each day windows is closer to dissapear... :D 

Greetings!!

---

### Post by samir85 on 2006-05-08
[QUOTE=Blashyrk]Very very very good news!! I have tried smartdimmer and works perfectly. I'll try to bind them to F5 and F6 keys. 

And another very good news. With the new kernel 2.6.15-22 the wireless is working!!! (ole, ole, ole). Each day windows is closer to dissapear... :D 

Greetings!![/QUOTE]

I also own a sony vaio vgn-fe11h laptop,
how can I get smartdimmer working ? (I'm using Ubuntu Dapper)

btw: wireless is is really working out of the box now, unfortunately there's a bug that wpa doesn't work :(

---

### Post by Blashyrk on 2006-05-08
[QUOTE=samir85]I also own a sony vaio vgn-fe11h laptop,
how can I get smartdimmer working ? (I'm using Ubuntu Dapper)

btw: wireless is is really working out of the box now, unfortunately there's a bug that wpa doesn't work :([/QUOTE]

One of the recent updates installed me automatically (if you look for smartdimmer in synaptic you will find it) So if it's already installed try to execute
```
/etc/acpi/sonybright.sh up
```
or
```
/etc/acpi/sonybright.sh down
```
It shows me an access deny warning but it works. (With sudo you will not have any problem)

All this is very well explained in roby811's [blog]("http://1spray.splinder.com/") but it's in italian (I'm spanish so i did not have too much problems to understand it)

At least i only bind the commands to F5 and F6 keys with xbindkeys (it's in the repository)

Sorry for my terrible english :( I would like to write (and speak) nicely in shakespearre's language

---

### Post by sk0rp10 on 2006-05-08
for english readers here is sony fe11x howto: 

[http://www.iwebyoumind.com/index.php?codice=1143213731&SID=guest&lang=en]("http://www.iwebyoumind.com/index.php?codice=1143213731&SID=guest&lang=en")

enjoy it

---

### Post by theBuggane on 2006-11-04
Just to top this thread off, all is well now with my FE11S!

Edgy, acceleration, sound, screen dimmer, dual core, wireless...

Edgy's great & thanks for all the tips.

:)

---


---
title: "new Asus Laptop won't run linux U50F intel i3"
date: 2010-01-20
forum: Hardware
---

### Post by iconoclast88 on 2010-01-20
I purchased a new laptop from Best Buy on monday. I'm a huge asus fan and had to have one. 

So I downloaded Ubuntu 10.4 alpha 2 64 and burnt it and laoded it up and the installer worked fine. When I rebooted to use ubuntu the firs ttime, it froze during bootup at a black screen. Next, it got further and let me log in, but as soon as it did, it was froze.

The same behavior happens when I loaded the 32 bit version, and also earlier versions of ubuntu. Not to mention SUSE 11.2. It doesn't work. The only thing I could get to work that was stable is MEPIS linux, the latest release.

Is it because its a new chipset? the i3 from intel? I've seen not a lot on the i3, but plenty on i7 support for linux distros. 

This sucks, because I was hoping to finally be rid of windows dependence and go 100% ubuntu.

The model # is U50F-RBBAG05
The best buy link is:
[http://www.bestbuy.com/site/Asus+-+Laptop+with+Intel%26%23174;+Core%26%23153;+i3+Processor+-+Afterglow/9701922.p?id=1218158634004&skuId=9701922](http://www.bestbuy.com/site/Asus+-+Laptop+with+Intel%26%23174;+Core%26%23153;+i3+Processor+-+Afterglow/9701922.p?id=1218158634004&skuId=9701922)

Any help would be great. Thanks.

Josh

---

### Post by Weaselpants on 2010-01-25
Got the same problem.  This is the new Intel technology that has an integrated memory controller (no front side bus)  and has new chipset, storage (and probably other) drivers.  We are probably screwed  :( until a subsequent release.  If any developers are listening - please provide status.

---

### Post by Weaselpants on 2010-01-25
I heard from a guy on another fourm that he had the same problem.  seems that 9.04 loads, then you update to 9.10.  I am trying it now and so far it looks food.  livecd worked fine.  fingers crossed.

---

### Post by Weaselpants on 2010-01-25
Bad news - at least on my system - 9.04 works 9.10 does not.

---

### Post by iconoclast88 on 2010-01-26
Interesting. I'll try 9.04.

Under 10.4 a2, I also have boot issues as well as the audio not being recognized completely. For instance, i can play audio, but when i insert headphones, it plays it through the speakers and the headphones both.

I figured a new chipset would cause some issues. I just hope it doesn't take the next release to get support. If so, I'll be switching to the distribution of linux that supports it first unfortunately.

Josh

---

### Post by ishelu on 2010-01-27
Please, can you post if it works? 
I'm waiting for an i3 540 and I had not taken of the store til thursday 29. Maybe it's safer to stand for a Core2Quad Q8300 if the i3 doesn't work very well :confused: or we must wait til april the next canonical release:evil:.
Thank you):P.

---

### Post by mhauer4 on 2010-02-06
What I don't understand is if 9.04 works, why not 9.10? What broke or was omitted from the build?

---

### Post by iconoclast88 on 2010-02-08
FYI, 9.04 works alright. 
Not great, but ok. I can't update/upgrade the distro, obviously.
Video is ok. the resolution is limited because drivers aren't available that enhance it fully.

But power management works ok if I unplug the A/C, which was the biggest drawback in the later releases (9.10, 10.4).

I sure hope 10.4 official will have support for this laptop.

Josh

---

### Post by Zubb[RU] on 2010-02-08
I have Asus K40 AB series, and i have similiar problems: 9.10 install went fine, it runs but i can't install any new software (neither via USF nor directly downloaded) and i have headphones problem too.

I'm knew to Ubuntu world, so can someone explain how our problem can be solved and what can we do - or we just sit & wait for developers to fix it?

---

### Post by 401 Stargazer on 2010-02-13
I've got a new Toshiba running the new i3 as well. Same things as already noted, 9.10 just locks up with no display and 9.4 doesn't perform much differently. Sucks too, I couldn't wait to see Ubuntu on this machine after running so well on my old Intel Celeron with 1 gig of ram.
 
I think we'll have to wait for updates from Ubuntu, and most likely 10.4 before the OS catches up to the hardware.
 
At least Windows 7 is far better and stable that the last one. It will get me by for a little while until Linux is fully compatible.

---

### Post by L815 on 2010-03-06
I recently bought an asus u50f laptop. 

I had trouble with:
*buntu's x64 9.10 
Fedora 12 x64 
Fedora 13 x64 

Although, I did install Ubuntu Lucid Lynx without any issues. Everything seems to work fine.

---

### Post by plus20db on 2010-03-24
I have an Asus U50F and I am unable to boot from any CD.  I am able to enter BIOS and check the settings, which include the DVD ROM/Burner as a boot device.  In windows, I can read and burn CD's with no problems.  I've played with the boot sequence in BIOS (although it was correct to begin with; first checking the DVD for a CD) however, still won't start up booting from the CD, although the laptop does spin up the DVD during the BIOS boot.  Did you guys do anything special to get your laptops to boot from CD Media?  Any help would be great, as I'd like to install any Ubuntu version that may work...

---

### Post by YuraYong on 2010-05-30
just tested my new asus a52j laptop with ubuntu netbook 10.04  working fine except cannot find driver linux type for my ati mobility radeon hd 5145 :popcorn:

---

### Post by Peter Shea on 2010-06-06
I love the Asus U50F but wonder how long I'll be stuck "exclusively" with Microsoft.  Was looking forward to at least dual booting with Linux.  Do *any* distributions other than Ubuntu work with this Taiwanese beauty?

---

### Post by KiDQUiCK on 2010-07-03
I recently got a refurb Asus U50F... loving it! All works well with Ubuntu 10.04 Karmic Koala, with the exception of suspend/hibernate. :\

Confirmed that the i3 chipset works fine with kernel 2.6.32 64-bit.

---

### Post by ralpyka on 2010-07-05
Hi
I have a Toshiba L650, i3 330M and ATI HD5145.
The Ubuntu 10.04 and 10.10, fedora 13 doesn't worked, the system doesn't started. I think the problem is with the kernel.
I could install Ubuntu 9.10 from the alternate cd, and from terminal install the ati driver. All things was good, but after a restart, wasn't picture again, only a black screen.
What can I do?

---

### Post by mikerev on 2010-07-10
> **KiDQUiCK said:**
> I recently got a refurb Asus U50F... loving it! All works well with Ubuntu 10.04 Karmic Koala, with the exception of suspend/hibernate. :\

Confirmed that the i3 chipset works fine with kernel 2.6.32 64-bit.


I actually fried my battery on my u50f because of the suspend problem. I had to leave in a hurry and after a fresh install of ubuntu i manually suspended it, closed the lid, put it in my backpack in the laptop compartment and it got so hot that it killed the battery. Did you ever find a fix for it? I got a new one but I am going OCD with paranoia and manually shutdown -h'ing all the time.

---

### Post by holao09 on 2010-07-26
I've alread bought new laptop from asus(taiwan).
It's asus k40ip.
intel celeron t3300
ram 2gb
chipset nvidia g205m
hdd 500gb
but i can't run any linux or winxp on it
i try to install xubuntu ,kubuntu , .......any version not work
only gos 3.1 work but superbad .
What happen from may laptop?
Anyone can tell me?

---

### Post by hadji457 on 2010-07-27
I have installed Ubuntu 10.04 DVD on my Asus U50F-RBBAG05 and it works okay. The live cd did not work so good. But there are issues.
1. Will not suspend or hibernate. Crash.
2. If I pull the power plug to run on battery, crash.
Not sure if these are acpi or video card issues, or both.
 Having said that, video w/3d acceleration works at 1366x768. Audio works. Wifi works. Elantech touchpad is flaky but usable.
 Ubuntu runs very nice and snappy. Boots up quickly and seems to use a lot less resources than Win7.

---

### Post by andydch on 2010-07-27
i have same problem, acpi problem on ubuntu lucid 64bit
fan is not working, no suspend/hibernate, can't adjust brighnest, only 1 processor running

my laptop is toshiba satellite L510 with i3

:(

---

### Post by holao09 on 2010-07-27
i've already install mepis .
it's not good !
no graphics----vesa 8-x
wrong sound!
it's so sad!

---

### Post by JustusLibertas on 2010-10-04
SUSPEND now works on my U50F-RBBAG05 thanks to this post: [http://ubuntuforums.org/showpost.php?p=9180298&postcount=7](http://ubuntuforums.org/showpost.php?p=9180298&postcount=7)

Woohoo!

---

### Post by JustusLibertas on 2010-10-04
FYI: found the headphones fix


[http://www.reddit.com/r/linux4noobs/comments/d7hak/would_some_of_you_be_nice_enough_to_help_me_to/?sort=old](http://www.reddit.com/r/linux4noobs/comments/d7hak/would_some_of_you_be_nice_enough_to_help_me_to/?sort=old)
[https://bbs.archlinux.org/viewtopic.php?id=103470](https://bbs.archlinux.org/viewtopic.php?id=103470)

---


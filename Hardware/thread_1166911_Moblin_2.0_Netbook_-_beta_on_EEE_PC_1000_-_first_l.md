---
title: "Moblin 2.0 Netbook - beta on EEE PC 1000 - first look"
date: 2009-05-22
forum: Hardware
---

### Post by milanlin on 2009-05-22
I have been looking forward to Moblin to get an Intel optimized netbook OS.
Suddenly they surprised with 2.0 beta version. I would call it alfa 2, because the interface is redesigned and it has far to stable release. I am testing it on EEE PC 1000 +++++ now. Currently I am happy with Eeebuntu core 3.0 +++++.

**Installation:** ----- I wanted to install Moblin on second partition of second hardrive sdb2 and keep other os on sdb1. I have tried a lot of possible combinations of sdb2 - unformatted, ext3, ext4. **Partitioning:** ----- by installation was finished with errors. So the only way to work it out was to use all sdb and kill other system. 
I have used installation cd and my first installation ended in the middle with message that the image is corrupted.

**Booting:** +++++ Oh yeah, that is what we need from Intel = very fast.

**Interface:** :o

**The theme** +++++ is using black & white colors and looks very pleasantly with animated white wobbly **icons** +++++ in the top of black panel or dashboard. It is eye catching on white EEE PC and I can imagine that it fits on black netbook as well. It is really tempting me to try this theme in some other gnome distros, I hope it is possible.

**Top menu (dashboard??)** ++ The panel is auto-hiding when it is inactive. To activate and scroll down the panel you traditionally point cursor in the top of the screen. The default menu structure represents that Moblin is aiming to go somewhere very close to cloud - my zone, twitter, messenger, internet, media, pasteboard. I am missing 
**customization** ----- of this top bar and fast access to the applications. Scrolling down through the apps menu takes too much time. Gnome-do +++++ or some command line would be useful. 

**Pasteboard** ++ I have found it useful in this environment due to lack of right click, but it is not necessary. Twitter --- well, if somebody like to spend the time this way but in a default layout??? 
Navigating through **zones** +++++ which are the opened separate applications is done probably via 3D wall effect. 
In the **media** +++ menu you can find again beautiful animations.
**Internet** ++ the chrome style Moblin browser is contracted to yahoo. The highlight color should be more visible in navigation toolbar. There is Firefox in apps as well.

**Graphics driver** +++ It looks that it is working out of the box when there is a support for animations, but I am not definitely sure, because some frozen snapshots or screen leftovers are appearing on the desktop.  And again dear Intel here people will request the best from Intel. This is not the best. 
**Flash and Java** - not tested yet - write your comment please.
**Applications management**  based on fedoras yum but lack of basic software in default repositories. 
**Bugs** -------- There is a lot of things to fix, implement and change and many times you meet misbehavior, unstable behavior or no response from basic buttons and keyboard shortcuts like save or close at this beta stage. But it is a give and get back attitude to report the bugs simply by clicking the send button.
**Functionality** ----- Well if we will define netbook as a shrinked laptop for a cloud computing and basic internet and multimedia needs then Moblin 2 will try to speak loudly to the vendors and it has got potential to be a lovely gnu/linux distribution. I am also very interesting on moblinized Suse. But if somebody wants more from Intel Atom 270 then Eeebuntu 3.O core is still better than netbook remix.

Please - do you know where are any turn off, log off buttons??? Well as a new user I can not locate it. 

Thanks for your opinions and discussion. Feel free to correct me where needed.

---

### Post by snowpine on 2009-05-22
Press the power button to shut down. 
I find Moblin intriguing but much too buggy to install. I would install it on a USB stick or SD card, but their installer does not currently allow this. There is no way I'm replacing my nice stable Debian install with Moblin. ;) If they get the USB/SD install working, I would definitely help test Moblin.

---

### Post by milanlin on 2009-05-27
**OPENSUSE-MOBLIN-0.0.2**

How in the world we gonna make everything alright?
How in the world we gonna make everything in time?
Train burning, all night burning...
Trainfire up and down the line.

Raw Opensuse is wearing Moblin suite and Novel needs to be in the train. 

I was quite enthusiastic with Moblin 2.0. Opensuse-Moblin should bring some handsome implementation of Moblin 2.0. So very quickly I have put my hands on it and just 15 minutes was more than enough.
Network manager is not able to establish any connection at all.
Applications menu is messed up, duplicated entries, it is wide and not implemented into the zones structure yet.

**Verdict: Unusable!!!!** Nothing new just the effort to be there!

---

### Post by binbash on 2009-05-27
I tested it with a notebook (not netbook :) ) EVERYTHING works out of the box, the only thing which sucks was low sound.BTW it has a good interface

---

### Post by cimh on 2009-10-01
> **milanlin said:**
> I have tried a lot of possible combinations of sdb2 - unformatted, ext3, ext4. **Partitioning:** ----- by installation was finished with errors.

On my 901 the install failed at the partition stage with curruption errors. This happened every time I tried with different options. This means the ssds are messed up and have to be reformatted The only way i could solve the problem was to do a fresh ubuntu install and forget about moblin. 
 - you have been warned!

I didnt do a checksum check (I never do with distros)so it might be my fault but the formatting section of the install process wasnt good you were not given much control (Also surprised to see it doesnt give you an ext4 option) 

Its a pity because 2.o looks good and runs great in live mode. It has a package manager and a few programs to download. I'm not keen on the drop down menu - its a pain when you want to access the top of the screen - its catchy but i think the standard linux panels and menus are neater.

cimh
901 karmic beta

---


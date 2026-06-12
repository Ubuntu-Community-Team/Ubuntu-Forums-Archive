---
title: "upgrade celeron m cpu (no pae) with pentium m 760 (pae enabled)"
date: 2014-10-10
forum: Hardware
---

### Post by Jon_Trofler on 2014-10-10
Hello, I installed Ubuntu 12.04 on my old XP machine and like it so far. Just seeking a little feedback before I spend $14 (not that it's a lot) on this ebay Pentium M 760 CPU. I want to know if the wattage difference between the two chips will be an issue. The Celeron M runs at 21w and the Pentium M at 27w. From what I've read so far it's not an issue except for maybe slighty reduced battery time. Everything else seems to be compatable with my 9 year old Gateway M320 motherboard. The main reason for the swap is the Pentium M 760 is listed as PAE enabled (which should allow me to install the 14.04 update?) with the added benefit of a faster clock (1.3 vs 2.0). Any responses will be appreciated, hopefully I posted it in the correct area ;)

---

### Post by sudodus on 2014-10-10
Pentium M 760 CPU has more horsepower than the older Celeron M at 1.3 MHz :-) The difference in power usage is rather small, and should not be a problem.

But I think both CPUs have PAE capability. Many older Pentium M and Celeron M CPUs have PAE capability but lack the PAE flag.

You can try to install Lubuntu or Xubuntu 14.04.1 LTS with the boot option **forcepae** according to this link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

See this link for more background

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

---

### Post by Jon_Trofler on 2014-10-10
Thank you for responding. I've tried everything to enable or force PAE on this Celeron (I guess it is capable but not switched on). I have been able to use the force PAE command once but that was only on the very first Ubuntu install (Zorin). The Pentium M 760 is actually listed as having PAE enabled "out of the box". Switching it out seems the easiest way especially with the added clock speed and L2 cache. Thanks again for your input, I'm going to put $14 on the line (thermal paste included!) and try the upgrade :p

---

### Post by sudodus on 2014-10-10
Good luck, and please share your result with our community :-)

---

### Post by Jon_Trofler on 2014-10-10
Thanks again, I'll update in about a week when the part is delivered.

---

### Post by tgalati4 on 2014-10-10
Make sure the height of the installed processor is the same as the old one.  Most laptops use one headsink to bridge both the CPU and GPU.  If the Pentium M is taller, then that might create a tilt in the heat sink that prevents it from laying flat on both chips.  Check the dimensions of both processors.

---

### Post by Jon_Trofler on 2014-10-10
Thanks for the heads up but I think it has integrated graphics on the motherboard. There is only the CPU under the heatsink/fan.

---

### Post by coffeecat on 2014-10-11
You posted this in the Other OS section. As you are running Ubuntu...

*Thread moved to **Hardware**.*

Good luck!

---

### Post by Jon_Trofler on 2014-10-11
Thank you Coffeecat, I thought it belonged in "other OS/ projects" but I guess hardware is better. Thanks for the "good luck", have you heard of anyone else switching these two processors to solve the PAE issue?

---

### Post by weatherman2 on 2014-10-11
Your Celeron M (350?) has a 400MHZ Front-Side Bus (FSB) and the Pentium M 760 has a 533MHZ FSB.  This is important; the motherboard must be able to support the faster FSB.  If not, it won't work at all in your laptop.  The Pentium M 755 - also 2GHZ - has a 400MHZ FSB like the original CPU and in my opinion is more likely to work in your Gateway.

Also, the BIOS needs microcode for the CPU to work properly.  If possible, upgrade the BIOS to the very latest available from Gateway (now owned by Acer).   That gives you the best chance to support the latest CPUs.

I've done a lot of laptop CPU upgrades and I'd say the chance of this working is about 50-50.  These Pentium Ms do seem to have PAE enabled by default, so it ought to solve your problem there.

Make sure you clean the old thermal paste off the heat sink and use the proper amount of thermal paste (not too much) on the new one.  Clean all the dust out of the fan area and the whole heat sink when you open it up - these things can get dirty over the years and cause the CPU to run hot because it can't be cooled properly.

The 760 or 755 would be a nice performance boost.  You might in some ways see better battery life, because the Pentium M has better power management (Enhanced Intel SpeedStep Technology (EIST)) and would allow the CPU to draw less power at idle.  Under heavy use - yes, the Pentium M 760 running full speed might drain the battery a little faster.  Assuming the cooling system in your Gateway can handle it, the fan may run a little more often but otherwise you should be fine there.  The Pentium M 755 should offer better battery life than the old Celeron M thanks to the EIST.

---

### Post by Jon_Trofler on 2014-10-11
Hi Weatherman2, thanks for the information. The website "cpu upgrade .com" has the chances at 63% based on all motherboards produced.I don't know how accuate they are but I'm kinda happy with 50/50 at this point, lol. I was originally going to order the 755 because it runs at 400mhz but the wiki for Pentium M cpu's didn't have the 755 listed as pae enabled as default. Only the 730, 740, 750, 760 and 770 have pae enabled and all run at 533mhz. If the chips weren't so cheap I probably wouldn't try this without being able to send them back. I actually found a "760 two pack" on eBay for $14. Most people are listing one for $14 so I guess I could make a couple bucks puting them back on eBay if they don't work. I'm really hoping this motherboard supports the higher mhz because the laptop still works great (and it's fun to work on). Thanks again for the input, I can't wait to try this.

---

### Post by weatherman2 on 2014-10-11
You're right, it looks like none of the versions of the 755 (there are two) are supposed to be PAE-enabled.

However, it looks like the Pentium M 745A (1.8GHZ) is the C0 stepping - and that's where PAE is supposedly enabled.  Check out this page if you haven't already:

[http://en.wikipedia.org/wiki/List_of_Intel_Pentium_M_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Pentium_M_microprocessors)

I see a SL8QZ (Intel part number) for the 745A on eBay for $14.49 (with shipping) from the US.

I can't guarantee that one will work in your laptop either, but it is 400MHZ FSB.

---

### Post by Jon_Trofler on 2014-10-11
That's interesting. I didn't know enough about cpu's to have gotten into the "C0" thing. That sounds promising and gives me hope that there is another option if the 760 doesn't work. With the 745A operating at the same watt and mhz I would have ordered that one if we had this conversation earlier ;). One question: the BIOS says CPU speed is 1300mhz. How does that factor into the equation? Thanks for your insight.

---

### Post by weatherman2 on 2014-10-11
1300MHZ = 1.3GHZ.  When you install the new one - assuming it works - it should say 2000MHZ in BIOS.

I wouldn't worry much about the "extra watts" of the 760 if it works at all.  As I said, when idling, it should eat less power than the Celeron M does.  That's because EIST lets the Pentium M slow down much more than the Celeron M can - and when CPUs slow down (when not doing anything), they use less power.  Celeron M is a budget CPU which had this EIST feature intentionally excluded ("if you want more features such as better power saving, pay more.").

---

### Post by Jon_Trofler on 2014-10-12
1300mhz = 1.3ghz. Duh, that makes sense. I feel kinda dumb :p. About a month ago I bought a stripped Gateway M320 off eBay because my laptop's charge port was cracked and loose. I figured that would be easier than taking the entire thing apart to repair it. Everything plugged in quickly and worked perfectly. Now that I'm attempting this CPU upgrade I actually looked at the motherboard serial numbers. My old one ends with B400 and the newer one ends with B500. All other numbers and letters are the same. Does that possibly mean that the newer board supports 533mhz fsb and the old one 400mhz? I'm just trying to clear this up before I plug in a CPU that damages it or the motherboard. Can anything be damaged from an unsupported mhz when I power it up? I've read that it can. As you pointed out, there are a few 400mhz chips that are C0 but it appears that this new board supports 500mhz. This is what I found on a website called cpuworld. Thank you for your time.

Celeron M 300 series or Pentium M: 
[LIST]
[*] If your motherboard supports 533 MHz FSB then the fastest upgrade option is a Pentium M 780. If the Pentium M 780 seems too expensive or difficult to find then consider upgrading to Pentium 770.
[*] If your motherboard supports only 400 MHz FSB then the fastest upgrade option is a Pentium M 765. If the Pentium M 765 seems too expensive or difficult to find then consider upgrading to Pentium 755.
[/LIST]

---

### Post by weatherman2 on 2014-10-12
Do you mean model numbers, not serial numbers?  If you can find the exact specs of that model number, you may be able to figure out what FSB it will support.

But there is no 500MHZ FSB - it would be either 400MHZ or 533MHZ (or 667MHZ, etc.).

Ultimately you'll just have to try it.  

I wouldn't invest much more in this old laptop, though - anything with only a Pentium M (single core CPU) is never really going to get that fast and will have limited upgrade options for RAM and perhaps hard drive (if not a SATA hard drive, you are very limited).

---

### Post by Jon_Trofler on 2014-10-12
Yes, the model number. I realize that there isn't a 500mhz fsb but would Intel choose to call there new mobo model number B500 or B533? I was just thinking that the B400 model number supported 400mhz fsb and when they came out with the one that supports both they just called it B500. It sounds logical as far as model numbes go. Would you be concerned about damaging anything if it doesn't support 533mhz fsb? That's the last question then I'll leave you alone, lol.

---

### Post by weatherman2 on 2014-10-12
No, I wouldn't be worried about plugging in a 533MHZ CPU and have it damage anything. It just won't work.  Plug the old CPU back in and it should work fine.

If you plugged in a different CPU that is way different from what your board supports - perhaps runs at a lower voltage - then in theory you could damage the CPU in that case, not the motherboard.  But you haven't mentioned any others that seem too far out of bounds.

---

### Post by Jon_Trofler on 2014-10-12
There are a few companies that offer an "ide pata ssd". I'm going to get a 64gb SSD for $57.00 new and I already maxed out the RAM at 2gb. Another $14 on a CPU was just part of the fun. I actually have two newer desktops running W7, an Acer W500 with W8.1 and a couple cheap 7" Android tablets. Because the laptop is old (and extra), this is the first time that I've been able to just screw around and learn to install different OS's and hardware. Pretty much all of this has just been a self imposed learning experience. When it's all said and done, I'll probably spend under $150. That's cheap considering everything that I've learned from people like you and the work itself. Thanks again for all your input weatherman2.

---

### Post by sudodus on 2014-10-13
I think you can do some testing while you are waiting for the new CPU.

In the opening post you wrote that ***Ubuntu 12.04 LTS works*** for you. I think that re-spins of Ubuntu with lighter desktop environments will work even better. ***Bento, Bodhi and LXLE*** are based on  Ubuntu 12.04 LTS (have the same engine under the hood), and they are likely to work well (and faster than standard Ubuntu, which is an advantage for example for watching video).

It is probably also possible to run ***Lubuntu and Xubuntu 14.04.1 LTS*** with the boot option ***forcepae*** (and maybe some other boot option depending on your graphics chip, for example ***nomodeset***). After such tests (live without installing), you will get a head start with the new CPU.

I refer back to post #2 and also to the following link

[URL="http://ubuntuforums.org/showthread.php?t=2230389"]Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it

[/URL]

---

### Post by Jon_Trofler on 2014-10-13
Goodmorning sudodus. I've installed a few 12.04 variations but they were all listed as non pae, Bodhi being my favorite. The problem with Bodhi is the family couldn't figure it out with the "fancy" interface that I preferred. For some reason everyone is now interested in the 9 year old laptop dad's been "fixing". I ran "more /proc/cpuinfo" command yesterday that showed the "flags" on my CPU, and PAE wasn't listed. I guess that's why the "force pae" command hasn't worked. I downloaded Lubuntu 14.04.1 and tried to install it using the force pae but it still gave me the "need pae screen". I think I've pretty much "proven" that this Celeron isn't pae capable. I'm actually very optimistic that the pentium 760 will work. Since I got a two pack I think I'm going to try them on both mobos so I can clear up this model number thing, B400 vs B500. If it doesn't work I will be getting the pentium 745A (400mhz) like weatherman2 suggested. Thanks again for the input, it has all been helpful and aided my "research" into antiquated, obsolete CPU's/mobos :p

---

### Post by Jon_Trofler on 2014-10-16
Good morning weatherman2. I received my Pentium M 760 chip a little early  and installed it Tuesday night with no PAE issues. The Gateway M320  really turned into a new(er) computer after the upgrade. Video was lag  free and Ubuntu 12.04 was super snappy. I went to bed feeling good.  Yesterday morning I installed Ubuntu 14.04 from disk and everything went  to crap. Super slow windows and animations along with occasional screen  "melting". I had all day so I installed Windows 8.1 (needed PAE before)  to see how that did. It was fairly functional, a lot better than Ubuntu  14.04. I then installed Ubuntu 12.04 and tried to upgrade to 14.04. I  was given a warning that my integrated graphics weren't up to the task  and I would have the experience that I mentioned above. I aborted that  upgrade and began a Lubuntu 14.04 install. The install was easy and  Lubuntu looks awesome, clean and simple. The two problems that I have is  the new Firefox URL bug and when I was using the terminal to install  the wireless cutter It wouldn't copy and paste to the terminal. Another  thing is that the chip is supposed to run at 2.0ghz but the BIOS is  showing 1500mhz, I haven't researched how to tweak that yet. All in all  it was very easy and inexpensive to upgrade the CPU. I haven't tried to  put the other chip into my old mobo (b400 model #). Just figured I would give you a heads up. I'll probably be opening a new thread for the new issues that I listed. The Firefox bug is really annoying, I might try to install the previous version. Thanks for your patience, have a good day.

---

### Post by sudodus on 2014-10-16
The new CPU works! Congratulations :KS

I'm sure you will fix the (minor?) problems ...

---

### Post by Jon_Trofler on 2014-10-16
Thank you sudodus, I'm really happy with the better performance! I think everyone with a Celeron M cpu should try this even if their graphics can't handle Ubuntu 14.04. I like Lubuntu, it's better than Zorin or Bodhi and video doesn't lag like before. The problems are minor but I really want to fix this Firefox bug. I couldn't find anything posted so I opened a new thread. Thanks again!

---

### Post by weatherman2 on 2014-10-16
It's good to know the new CPU worked!

I use Gnome Flashback and not Unity in Ubuntu 14.04, and with an old machine I'd probably choose the Metacity option for Flashback login, for better graphics performance.  I know Lubuntu is designed for slower/older machines, but I still much prefer regular Ubuntu with Gnome Flashback to Lubuntu.

But I plan to use 12.04 until end of life, anyway - April 2017.  Lubuntu 14.04 is also supported until only April 2017 (Ubuntu 14.04 until April 2019).  I don't have any particular desire to move up to 14.04 on my primary laptop but do have 14.04 on another machine I use regularly, just so I can feel "current."  12.04 works just fine.

---

### Post by Jon_Trofler on 2014-10-16
I'm very happy with the new chip! You were right about my cooling fan, it's working a lot better after I cleaned it with a toothbrush. There was actually too much dust build up to blast it off with air. After 9+ years it had stalactites hanging from it ;). 12.04 does work great and I probably wouldn't have "upgraded" except for your stated reason of feeling current. The main reason at this point for installing Lubuntu is I thought it might fix the Firefox bug, it didn't. Do you know why the BIOS is showing 1500mhz instead of 2000mhz? It's not a big issue because I'm happy with the performance boost already. Thanks for your feedback weatherman.

---

### Post by weatherman2 on 2014-10-16
To me, 12.04 is "current" enough.  I'm not the type of person who always has to have the latest/greatest of anything, and from my limited use of 14.04 so far (I use it every day on a server but not with much complexity), there isn't a whole lot of surface difference between 12.04 and 14.04 that makes me dying to switch (under the hood - lots of differences - but why do I care)?  12.04 is supported through 2017 so that's good enough for me.

I don't use Firefox regularly (I use Chrome) so I don't know what Firefox bug you are talking about.  (Sorry, I missed that part of the discussion.)  But, you can download and install any version of Firefox you want:

[https://ftp.mozilla.org/pub/mozilla.org/firefox/releases/](https://ftp.mozilla.org/pub/mozilla.org/firefox/releases/)

though you'll have to build it from the tarball from there.

It seems likely to me that the BIOS doesn't have your CPU in its list of known CPUs, so that's the reason it lists it at 1500MHZ.  But is it really running that slow?  (That's what really counts, right?)  Not sure.  What does Ubuntu say under "System Monitor?"

Is this the latest BIOS available from the manufacturer?

---

### Post by Jon_Trofler on 2014-10-16
I just ran "CPU Blowfish" because I can't find system monitor in Lubuntu. It says the cpu clock is at 600mhz and the processor is 1.5ghz. It's about 2-3x faster than the Celeron, no joke. Web pages pop up fast and YouTube videos don't lag now. I'm happy with it, I'm just wondering why it's not running at 2.0ghz. Gateway never issued a BIOS update as far as I can tell.

---

### Post by weatherman2 on 2014-10-16
It may not be possible for the laptop to run the CPU that slow (at 1.5GHZ).  I think the CPU multiplier is set in the CPU - to prevent overclocking, actually, but it would also prevent underclocking.  That CPU knows it is supposed to run at 2GHZ.  The only way to over/underclock a Pentium M, in my understanding, would be to change the FSB speed which also changes the speed the RAM runs at.  Run the RAM too slow (or too fast) and it might not be reliable.

Keep in mind that Enhanced Intel Speedstep Technology (EIST) enables the CPU to slow down to save power when not under CPU load.  The Celeron M does not have EIST, so it can't slow down (or not as much).  If Gateway never sold your laptop with a Pentium M, the BIOS may never have needed to deal with EIST.  Anyway, that could explain why you see different readings like 600MHZ - that could be when it is basically idle.

More likely, the CPU is really running (when it needs to) at the correct 2GHZ speed, but the BIOS thinks it is running at 1.5GHZ.  "CPU Blowfish" probably relies on the BIOS.  The problem is, the BIOS doesn't have any way to "time" a CPU to see how fast it is really running; instead, it relies on a look-up table, and it reads code from the CPU identifying it.  This CPU probably isn't in the look-up table, so it assumes it is 1.5GHZ.  But that doesn't mean it is slowing the CPU down to a maximum of 1.5GHZ.

That's why an updated BIOS might fix the indicator - which may not cause you any real problems if not fixed.  The newer CPU probably didn't yet exist when the last BIOS update was released.

You might post a further query over on a hardware forum like TomsHardware.com or AnandTech.com (or even an overclockers forum) to get a definitive answer.  I am guessing here.

The Pentium M will also be faster than a Celeron M because it has a larger cache, I believe, which would help performance considerably, even if the Pentium M were stuck at the same 1.3GHZ as the Celeron M.  You probably wouldn't see a 3X speed up from that.  Performance improvement varies depending on the code it is running - but 1.5X on average from a larger cache is reasonable.

---

### Post by Jon_Trofler on 2014-10-16
Hey weatherman2. I think I'm going to reinstall XP to deal with the BIOS. From what I've read it's probably the safest way. What do you think?

---

### Post by weatherman2 on 2014-10-16
Did you verify that Gateway (now Acer) has an updated version of the BIOS on their website, that is newer than the BIOS you have now?

If so, is the BIOS release date newer than the release date of the Pentium M 760?  If not, the BIOS may not necessarily know about that CPU, either.

Yes, installing XP is the safest way to update an old BIOS, if that's what the laptop came with.  There are other tricks to do it say from a DOS boot floppy or something, if the laptop has a floppy and you have a floppy and there is a version of the BIOS update that runs via DOS.  Yes, there are tricks sometimes to use a USB boot to simulate a floppy - but doing it from XP is probably safest.  There's always a small chance you could "brick" the laptop (render it useless) if you mess up the BIOS update.

---

### Post by tgalati4 on 2014-10-16
Search the web for how to make a freedos CD or USB stick.  You burn the image with your BIOS files and you boot off of it.  No need to use WinXP if you don't have to.  I've used this process several times.

---

### Post by weatherman2 on 2014-10-16
If Gateway/Acer released a Windows exe file intended to be run under Windows, it is risky to try to run it under FreeDOS.  You can probably extract the right ROM file(s) from it and use some DOS tool to do the flash, but I would not risk it personally.  Then again, I have spare hard drives, and re-installing Windows as a evaluation just to flash the BIOS is easy for me - I don't have to erase Linux, just swap the spare hard drive out.  Not everyone has that luxury, I know.

---

### Post by tgalati4 on 2014-10-17
If you run the Windows installer, you will often find that it just dumps flasher.exe and some ROM binaries to a directory, then runs a batch file to run flasher.exe with the ROM files.  So yes you are correct. Installing WinXP just to run some installer that simply dumps DOS executables increases the Agony Units.  If you have no other Windows computer to run the installer, then you don't have a choice.

---

### Post by weatherman2 on 2014-10-17
> **tgalati4 said:**
> If you run the Windows installer, you will often find that it just dumps flasher.exe and some ROM binaries to a directory, then runs a batch file to run flasher.exe with the ROM files.  So yes you are correct. Installing WinXP just to run some installer that simply dumps DOS executables increases the Agony Units.  If you have no other Windows computer to run the installer, then you don't have a choice.

Right - and as I said above, it's still a risk to try to run something like "flasher.exe" that was designed to run in Windows under FreeDOS.  It may not work properly and could brick your computer with a bad BIOS flash.

---

### Post by Jon_Trofler on 2014-10-20
Hey guys. I'm not going to mess with the BIOS at all. The laptop works well enough and I don't think that there is an updated BIOS anyway. Thanks for all the help!

---

### Post by mörgæs on 2014-10-20
The BIOS fear in Ubuntuforums is approaching paralysis. It's fine to be careful but within reasonable limits. 

I would say, google BIOS upgrade for your particular computer. If you don't see a significant number of failures then go ahead. I have probably done 50 times or more myself and never experienced any problems.

---

### Post by weatherman2 on 2014-10-20
> **mörgæs said:**
> The BIOS fear in Ubuntuforums is approaching paralysis. It's fine to be careful but within reasonable limits. 

I would say, google BIOS upgrade for your particular computer. If you don't see a significant number of failures then go ahead. I have probably done 50 times or more myself and never experienced any problems.

The "BIOS fear" is about using a non-standard, non-supported method to flash the BIOS, not about using a standard, supported BIOS flash method.  If the computer manufacturer offers a Windows exe file, it should be perfectly safe to run it in Windows.  Trying to exact the bin files and install them with some other method like FreeDOS is dangerous and should be considered an advanced option for experts only.

I would **not** "google BIOS upgrade."  Only get a BIOS update directly from the manufacturer's website!!  You may find other "BIOS updates" available from other sites that may not work at all on your machine and could easily brick it.  A BIOS is very specific to each individual motherboard model.  Even then, you may find motherboards with the same "model number" with different BIOS versions that are not compatible.

I have flashed many BIOSes too.  I've had one bad flash, when I took a chance (very similar to the OP's) and tried to install a non-standard BIOS.  The BIOS was for an Asus board with the same model number as my board, but my board was made by Asus for a Sony computer.  A CPU upgrade sort of worked but complained about an incompatible CPU.  Asus had a newer BIOS than Sony, for what appeared to be the same model Asus board.  I took a chance on the Asus BIOS - and it failed and bricked the board.  Even known techniques described by Asus for restoring BIOS from floppy failed.  Lesson learned.

---

### Post by mörgæs on 2014-10-20
OK, maybe I wasn't clear. By googling I didn't mean 'search for an .exe file' but 'search for which experiences users have been posting'. 

The new BIOS itself should always come from a trustworthy source.

---


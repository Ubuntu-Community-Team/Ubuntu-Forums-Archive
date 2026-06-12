---
title: "Cyrix MII won't install kernel"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by filbo on 2009-01-19
Hi --

My wife is trying to install XUbuntu 8.10 from the alternative install CD onto an old Compaq Presario 2266.  After this failed I spent some time poking around in the installer busybox.  I'm pretty sure this failure is generic across all types of Ubuntu install.

The install fails because it determines that the CPU is a lowly 486, and the Ubuntu generic kernel is built for studlier CPUs.  But the machine's actual CPU is a 166MHz Cyrix MII.  CPUID shows it as "CyrixInstead", family 6, model 2.  This CPU was shipped a bit after the Intel Pentium II and AMD K6 generations; it is effectively a Pentium MMX CPU.  I *think* Ubuntu's generic kernel is still supposed to run on this generation...

The decision to reject the CPU is made in a script function, arch_get_kernel_flavour() in /usr/lib/base-installer/kernel.sh, from _["bootstrap-base" package (v. 1.86ubuntu7_i386)]("http://packages.ubuntu.com/intrepid/i386/bootstrap-base")_.  This function recognizes CPUs with vendor strings of AuthenticAMD, CentaurHauls, GenuineIntel, and GenuineTMx86.  Anything else (e.g. this "CyrixInstead") is labeled a 486.  The installer then aborts since according to its notes, the "generic" kernel will not work on a 486.

I would like to both report a useful bug into Launchpad; and get this machine installed.  Which are two fairly different projects.

Before reporting a bug I need to know whether the "generic" kernel is actually built in a manner which would not run on the Cyrix MII family 6 model 2.  The script seems to allow any other known Pentium-or-later CPU to pass.  If this kernel should run, (*BUG*) the kernel.sh script should be modified to recognize "CyrixInstead".

On the other hand, if the "generic" kernel would *not* work, (*BUG*) the installer is at fault for not having available, and falling back to, the _[kernel-image-i386 package ]("http://packages.ubuntu.com/intrepid/linux-image-386")_.  Actually the installer is clearly at fault for that since I could actually be trying to install on a real 386 or 486.  So I'll report that unless I find an existing bug about it.

To install the machine I need to either twiddle the script to report that this CPU will work with the "generic" kernel; or make available the -i386 kernel packages.  In either case I need some guidance on points of leverage for getting this stuff into the action during an install.  I don't want to roll my own complete Ubuntu install ISOs, I want to leverage off the existing ISO as much as possible.

Proposed plan of attack:[LIST=1][*]get it installed with -i386 kernel packages[*]once installed, install -generic kernel packages and see if that kernel boots OK[*]if -generic boots, bugreport that Cyrix should be recognized by kernel.sh[*]either way, bugreport that installer should be willing to fall back to -i386 kernel.[/LIST]I need help with point 1 -- I know *what* to do but not *how*.  Please help.

Here's a previous user having this issue with Ubuntu 7.10: _[Trying to install XUbuntu command line system on old hardware but won't choose kernel]("http://ubuntuforums.org/showpost.php?p=3798693")_  (Both cases are with XUbuntu; this is because they're small weak machines, not because these problems are unique to XUbuntu.)

Thanks,

>Bela<

---

### Post by ymo on 2009-02-07
Congratulations on working out the source of this problem. A couple of days ago I dragged my IBM/Cyrix 6x86 MII PR200 system out of the basement and tried to install Ubuntu Server on it and got the same failure mode you found.

Today, thanks to you, I have successfully installed Ubuntu 8.10 server without needing to burn a new CD-ROM.

1) Start installation as usual
2) When you reach the disk partitioning stage, press Alt-F2
3) Press Enter to get access to shell prompt
4) Use the nano editor to add a CyrixInstead entry to /usr/lib/base-installer/kernel.sh that simply echos "586" (this was just a test - it should look at the family type as well).
5) Press Alt-F1 to return to partition setup screen
6) Continue installation as normal

I first tried this with echo "686" but the resulting system failed to boot reporting that the CPU was missing the "pae" capability. Dropping back to 586 gave me a working system.

I fully agree with you re the 486 - it should have worked. A 386 I am not sure about - I cannot even boot the CD on my 366MHz 486sx SoC as it reports a missing "fpu". A 386+387 combo might be valid.

P.S. It looks like the PAE problem is only because I used the Server Installation CD - a desktop kernel does not use PAE.

P.P.S. Of course these Cyrix systems do not actually meet the minimum requirements for Ubuntu (see [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements) for details). It states "300 MHz x86 processor" as a minimum.

P.P.P.S. Reading further shows Xubuntu has a 166MHz CPU minimum. Also a 486 is listed as absolute minimum spec CPU so it looks like the 386 is out.

---

### Post by filbo on 2009-02-14
Thanks for the instructions -- the key was knowing where to find the file in an editable state while booted into the installer.

But a funny thing happened on the way to the party: I had decided to install Jaunty [alpha 4], and kernel.sh seemed a little different.  There still wasn't an explicit mention of CyrixInstead, but kernel.sh ended up picking the -generic kernel rather than -i386.  Which is good, since only -generic is present on the install media.  (Actually I didn't check that, it's also possible someone added it back to the alternate CD.)

So, whoever read the initial report and fixed kernel.sh, thanks!

486 and 386 should work.  Requiring an FPU is a little odd since I think the Linux kernel internally disciplines itself not to use any FP at all; but so be it.  It's reasonable to say that if you really must drag out an ancient 386/486 box, it has to have the corresponding FPU.  FPU was separate with the 386, integrated with the 486.  "486sx" was a special crippled 486 with the FPU fused off, then you could install a "487" chip into an "FPU" socket.  I suspect the 487 was also a crippled 486 with the base CPU fused off.  They might even have done this as a way of increasing production yields, making slightly damaged units salable.  In any case, it confirmed that the "sx" suffix simply meant "sucks"... 386sx was a 386 with 16-bit external bus (vs. normal 32-bit); then 486sx comes along with a different form of damage.

Regarding the 300MHz "minimum" / 166MHz for Xubuntu: those are comfort limits.  The system doesn't check that they are met, nor does it have more subtle dependencies on CPUs that fast.  Those simply represent the developers' guesses about how slow a CPU will be tolerable.  And they're not far off -- Xubuntu with this 225MHz Cyrix MII is right on the edge of unusable.  Supposedly the MII is a bit more efficient per cycle than a same generation Intel chip, this can be looked at as approximately 300MHz worth of juice.  I'm sure someone somewhere would be able to tolerate half this speed; not me.

Oh, and come to think of it there might be a legitimate reason that 386 is absolutely forbidden.  I'm not sure there was ever a 386 motherboard that supported >16MiB RAM.  A bare Linux kernel and (say) busybox can certainly run in 16MiB, but anything that you could plausibly call "Ubuntu" requires much more.  Also I don't think any of the installer modes can run in so little memory...

Well, check that, I found a few 386 motherboards that support up to 128MiB: [AMI "80386 Baby Screamer LC"]("http://www.artofhacking.com/th99/m/A-B/32997.htm"), [Diamond Multimedia Systems "FastBus VLB"]("http://artofhacking.com/th99/m/C-D/31591.htm") -- and even one supporting up to 512MiB and (I believe) dual 80386 CPUs: [Wyse Technology "Series 7000i model 740MP"]("http://artofhacking.com/th99/m/U-Z/33472.htm")!  Wonder what modern Linux would think of that sort of beastie.  I think it had MPS 1.1 in BIOS...

---

### Post by ymo on 2009-03-27
I just tried installing my Cyrix box from the Ubuntu 9.04 Beta server CD and it still fails to find a suitable kernel :(

---

### Post by spcwingo on 2009-03-27
I highly doubt that any of the *buntus will install on that machine...even the cli-only versions.  You might want to give Puppy, DSL, or Slitaz a shot.

---

### Post by filbo on 2009-04-01
> **ymo said:**
> I just tried installing my Cyrix box from the Ubuntu 9.04 Beta server CD and it still fails to find a suitable kernel :(
Well, I could refer you back to the steps given on Feb 7th, but since you wrote them I assume you will have succeeded in your install.

Rather odd that my machine now installs gracefully while you still have to override yours.  Wait!  While previewing this post I noticed you said "server".  That'll be a different install script and I guess it can be forgiven if all the server kernels are compiled for more modern CPUs than a 3rd string clone from 10 years ago.

Status of my install (same Compaq Presario 2266 / Cyrix MII 233MHz / 256MiB RAM):

- has been running xubuntu jaunty since Feb 14
- kept up to date (approximately daily) with jaunty dev cycle; no problems experienced due to that
- long struggle to get X working, resolved by adding something (would have to go look) meaning "use 16 rather than 24 bitplanes" to xorg.conf
- got sound working after another struggle to identify the sound chips.  Once ID'd as ESS 1878(?), snd_es18xx driver did the trick.  Card shows up in PnP (both lspnp and various places under /proc/bus/pnp and /sys/devices/...), but I never could convince it to load by an alias.  Have to explicitly load the driver.
- All components of XFCE are **unbelievable** pigs:
- xfce4-mixer, besides dumping core a lot, had a 52MiB working set (!!!!)
- gdm took ~4 minutes of heavy grinding to get from one logout to next login
- xfdesktop & xfwm are piggish and load far too many buffaloes of other junk
- xfce4-terminal 20MiB working set and astonishingly slow
- so went on a search and destroy mission, now running:
- icewm, a pleasure and tiny
- qamix, tiny and workable
- switching back and forth between wterm (tiny but weak) and mrxvt (small and good) (I installed and evaluated 15 or so terminal programs.  The grandparents, xterm and rxvt, both came in around the middle of the pack.  xfce4-terminal, the term program provided in xubuntu "for smaller systems" was by far the most resource intensive.  xterm is clearly the most solid and also passes most of vttest while none of the others even pretend to; but lags in features (e.g. no tabs, no transparency).  Now if I could find a terminal that would allow its status line to be updated without triggering scroll-to-bottom-on-write and/or unhighlighting the selection-in-progress, I'd be pretty happy...)
- xdm as login manager (used slim for a while but it's not so slim, and still had about 1 minute of lugging before next login.  With xdm and icewm I can logout and back in in 25 seconds, repeatably)
- pulseaudio came under my baleful eye because it suddenly decided that only root should be able to make sound, anyone else it would load up but pretend that "null sink" was the only available sound output.  Spent a couple days trying to figure this out, then ripped out pulseaudio; it was another pig anyway.  Now using bare ALSA.  One problem: gcompris not happy, runs at unacceptably slow speed unless started with "-m" (mute -- no sound).  May have to reload pulse and figure out the permissions issue...  Target audience of 2.5yo daughter complains about no sound in gcompris.  7yo daughter researches homework using google to fact-check the teacher.  The world is changing rapidly...

With all that surgery I got system overhead down from ~180MiB to ~50MiB (numbers off the top of my head).  Now able to run Opera and Firefox, kids games, etc. without feeling like I'm going to die of old age.  Amazed at how bloated the supposedly "reduced" flavor of Ubuntu is.  A simple exercise of seeking replacement components that aren't pigs cuts the desktop working set by about 75%.  Goes from guaranteed swapping to occasionally touching swap if I'm trying to do too much at once.

What's the point of these exercises?  Well, what I thought should have been a perfectly usable machine for my kids now is just that.  Perhaps more to the point, I will soon switch to some of the same components on my modern laptop, with every expectation that it will go from merely adequately fast to blazing.  Even though I *can* work with multi-millisecond lags in everything, I'm sensitive to them and would be much happier if everything was instantaneous.  I'm going to trade in the bling of compiz for the zing of icewm...

Current minor issue (the majors being out of the way): icewmbg does a crap job of displaying backgrounds.  I'm using a background out of xcfe themes called "hardy-something", it's a nice purplish curve with lots of color gradients.  icewmbg renders this as if it's severely chopped the color map.  So either I have to fix icewmbg or figure out how to convince icesession to use Esetroot instead...

>Bela<

---

### Post by david_halliday on 2009-04-06
This is not unique to Cyrix MII, myself and many others are trying to install on a Webpad (WebDT 366) that uses an AMD Geode CPU. This also failed install a kernel on 8.10 but was ok on 7.X.

Of note, the Geode can support plenty of ram to meet all minimum requirements but requires a 586 kernel 686 will not work. 

It looks to me like the 586 kernel is causing the problem. As the installer works ok I can only assume it is using a base 386/586 version.

D.

---

### Post by cyrixmii on 2009-04-25
i'm very glad that i've found this thread.
i've got a **Cyrix M II/PR300**,but i had never seccesfully installed a Kernel 2.6 Distro.
All the distros i've tried(Slack12.x, Debian4 ...) they just thought my CPU is "i486", 
I'm now using Slackware 11.0 which is kernel 2.4.33 and it reconize my CPU as CyrixInstead 6x86. but that system is not very stable now. i'm tired of "./configure && make && make install".TOO SLOW!
So i'm thinking of install new version now so i could use repos instead of conpiling. 
then i found this post. i never thought kernel 2.6 linux could installed on a Cyrix MII CPU.

so i follow the instruction you guys talk about.
but it never really worked.

following errors were encountered recently:
xubuntu 9.04 alternate : boot cd error [**BUG INT:6 CR2**]
ubuntu 8.10 server: same as above
ubuntu 8.04.2 lts server: same as above
debian 5 : same as above

ubuntu 6.06.2 lts server: installed ok, but cannot boot into system, error [**BUG: soft lockup detected on CPU#0!**]
ubuntu 6.06.1 alternate: same as 6.06.2

i just want to use this system as a amule download machine.

P.S. i'm using SCSI harddrive instead of IDE hdd. adapter card : **Adaptec 2940UW**

could someone tell me what to do?

thank you very much for your patience

---


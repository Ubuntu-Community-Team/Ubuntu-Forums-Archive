---
title: "old distros"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by tednugent on 2009-06-25
Hello all I ahve a laptop that worked flawlessly with 6.1 and 7.1 but I have had nothing but trouble with 8.4 and 9.4. 8.4 froze up on a continual basis and 9 has wireless problems (constantly wanting me to put in my wep passphrase,and with fonts both in firefox and ubuntu.
I was wondering if I could load an old distro (preferably 6.1) and still be able to get the aplications I want,codecs,google toolbar,etc etc I loaded it up just prior to trying a fresh install of 9.4 and it worked well loaded fast wireless worked but i was unable to get codecs,google toolbar working (at least in the short time I fooled with it) So I guess my question is can it be done or would I be wasting my time trying to fool with it. I need an operating system that works with the little laptop and windows is out of the question. Thanks in advance

---

### Post by spcwingo on 2009-06-25
The laptop in question doesn't happen to have ATI graphics, does it?  I just finished installing 8.04 (Hardy) on my mother-in-law's laptop that has an ATI graphics card.  She was experiencing the same problems that you describe (apps crashing, lockups, etc).  All I did to correct this problem was edit her xorg.conf (/etc/X11/xorg.conf).  Under the Device section I added one line.  It now looks like this:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection
```

After a reboot the problems vanished...she even noticed a responsiveness boost to boot!  :D  Just be advised that compiz will not work with the vesa driver and this method may not work on 8.10 and later (different xorg version).

---

### Post by Mighty_Joe on 2009-06-25
Old distros will be problematic because they will not have the latest versions of software, security updates and a large community using and supporting them.
Stop by the [Ubuntu Wiki LaptopTestingTeam]("https://wiki.ubuntu.com/LaptopTestingTeam") and see how well your machine is supported.
Search this forum and [Launchpad]("http://launchpad.net/") and see if others with your hardware are having the same problem and if workarounds have been figured out.

---

### Post by tgalati4 on 2009-06-25
Although they won't receive updates, an older stable distro may work better with your machine.  You can always compile from scratch those applications which you want a newer version of.  Using the backports repository will capture some of the more popular packages.  For those packages that have not been backported, you will have to backport yourself.

As a general guideline:

Find the source code for the "must-have" application.
Unpack in your home directory or Desktop.
sudo apt-get install build-essentials
./configure
make
sudo make install

You will encounter lots of warnings and errors.  Errors need to be fixed in order to successfully compile a program.  Most warnings can be ignored--as long as the program works as intended.

Post your specific problem when compiling--there's usually a work-around.

---

### Post by timcredible on 2009-06-25
if the problem stems from the fact the the machine doesn't have enough memory, or isn't fast enough, i would suggest running a lightweight distro rather than going back to an old version of ubuntu.  personally, i like puppy real well, but there are a few others.  maybe just not running gnome might be enough, you could try xfce, it's in the repos.  to do that, install xfce via synaptic and then choose it at login.

---

### Post by tednugent on 2009-06-26
thanks ,Puppy looks promising as my laptop is older with only 512 mb of ram this was one of the reasons i began using ubuntu in the first place (besides hating windows with a passion)now if i can find the time to install it on my hardrive.can you load all the codecs necessary for radio streaming etc etc etc?

---


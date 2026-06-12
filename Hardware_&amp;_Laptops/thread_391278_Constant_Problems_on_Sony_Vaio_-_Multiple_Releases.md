---
title: "Constant Problems on Sony Vaio - Multiple Releases"
date: 2007-03-23
forum: Hardware &amp; Laptops
---

### Post by Darksword on 2007-03-23
Back in 2000 I bought myself a Sony Vaio laptop that came preinstalled with ME.  I used it off and on for years, but grew sick and tired of ME's legendary failures.

After an absolutely stunning success with Ubuntu 6.10 on a new Compaq desktop, I decided to dig the old laptop out and smack 6.06 on it and see if it would work.  It seemed to... at least at first...  And that's how this all started.

The system specs are:  733mghz P3, 128mbs RAM, 15 gig HDD, and 4X CDRW+DVD-ROM

First thing I did was scandisk and defrag in ME, then I repartitioned the HDD with Partition Commander and set up a dual-boot with ME and Dapper.

It seemed to work flawlessly at first.  Both OSs ran okay, and after much agony I found a D-link WiFi card with an Atheros chipset that worked out of the box.  It seemed perfect...for like 2 days.  Then things started going wrong.

When I booted into Dapper, it would fail startup roughly 3/5 of the time.  It would hang on "Loading Hardware Drivers" or "Loading Network Drivers" or "Loading Restricted Modules" whenever I tried to start it.  I would make it past that and the login and display managers would crash.  Totem and Openoffice would crash trying to open.

ME wasn't any better.  The entire system would lock up if I tried running any .exe files.  Opening Firefox or Windows Explorer was an instant BSOD.

Finally Dapper gave me a kernel panic error that was permanent.  I gave up, wiped the entire HDD, and did a clean install of just Dapper.  No more dual-boot.  Got my WiFi up in about 10 minutes, did a couple updates, and it seemed to be perfect.  This time it lasted for a week of casual use, not installing or uninstalling anything.

"Loading Hardware Drivers -- FAILED
Loading Network Drivers -- FAILED
Loading Restricted Modules -- FAILED

Loading Hardware Drivers -- FAILED
Loading Network Drivers -- FAILED
Loading Restricted Modules -- FAILED

Loading Hardware Drivers -- FAILED
Loading Network Drivers -- FAILED
Loading Restricted Modules -- FAILED

Loading Hardware Drivers -- FAILED
Loading Network Drivers -- FAILED
Loading Restricted Modules -- FAILED

BASH ~//hda01/dev-null PERMISSION NOT GRANTED
BASH ~//hda01/dev-null PERMISSION NOT GRANTED
BASH ~//hda01/dev-null PERMISSION NOT GRANTED
BASH ~//hda01/dev-null PERMISSION NOT GRANTED
BASH ~//hda01/dev-null PERMISSION NOT GRANTED
BASH ~//hda01/dev-null PERMISSION NOT GRANTED
BASH ~//hda01/dev-null PERMISSION NOT GRANTED
BASH ~//hda01/dev-null PERMISSION NOT GRANTED

Display Manager has crashed, returning to login screen"


So, fed up with Gnome  and Dapper I got the special installer for Kubuntu 6.10 and gave that a try.  I had no less than TEN installation errors.  At one point, the first time it started the partition utility, the system crashed so hard I couldn't even power it off at the switch.  I had to rip the battery out.  Several items in the installation failed, including installing the kernel!  The installation of basic programs also failed twice, and several individual items in hardware detection failed and had to be repeated.

So after 2 hours it finally installs and boots, albeit with some horrible epileptic flashing Matrix screens going.  KDE loads up okay, but I can't get it to find my WiFi card.  I take a break and when I power it on later, I try to log in and get that 

BASH ~//hda01/dev-null PERMISSION NOT GRANTED
BASH ~//hda01/dev-null PERMISSION NOT GRANTED
BASH ~//hda01/dev-null PERMISSION NOT GRANTED
BASH ~//hda01/dev-null PERMISSION NOT GRANTED
BASH ~//hda01/dev-null PERMISSION NOT GRANTED
BASH ~//hda01/dev-null PERMISSION NOT GRANTED
BASH ~//hda01/dev-null PERMISSION NOT GRANTED

error scrolling down the screen.  After ctrl-alt-deleting it THREE TIMES, it finally gets to the login prompt.  That's where it is right now.

---

### Post by daller on 2007-04-09
Since both ME and Ubuntu failed on you on the first try, and afterwards it still fails when only trying to install Dapper, I'd guess that there's something wrong with your hardware!

Have you tried installing ME alone? - Does that also crash?

My guess would be that your harddrive is "dying"... I've tried that twice, with some of the same things going wrong!

---


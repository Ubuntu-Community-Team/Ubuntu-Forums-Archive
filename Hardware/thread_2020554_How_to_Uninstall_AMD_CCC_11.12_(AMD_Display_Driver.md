---
title: "How to Uninstall AMD CCC 11.12 (AMD Display Driver ver 8.92)"
date: 2012-07-08
forum: Hardware
---

### Post by Johnny M! on 2012-07-08
Sunday 8-July-2012   14:30hr Local US Eastern
------------------------------------------------------------
Ubuntu 10.04 Up-to-Date (Kernel 2.6.32-41)


Help if able.

How do I uninstall AMD CCC 11.12 (AMD Display Driver ver 8.92);
so
I can install the soon to be released AMD CCC 12.7 Video Driver Package ?

Please confirm - Do I need to uninstall the current video driver before installing an upgraded one in place of it;
or
can I install directly over-top (overwriting) the old driver ??
Note: My Windows experience would suggest that an uninstall (before reinstall) is Necessary ! 

My current AMD Display Driver was installed by directly downloading it from:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
to the Desktop and executing the Install routine (No Package Manager and No Terminal Command Lines were used).   This was done following a Hardware Upgrade to the XFX Radeon HD 6870 2GB Video Card.

I have read all the Tech-Know-How of uninstalling the AMD proprietary "fglrx";
but
I am NOT using fgrlx !


So again, how do I (if necessary) uninstall AMD CCC 11.12 (AMD Display Driver ver 8.92) ?

Many Thanks in Advance !
:lolflag:

BVR
Johnny M!

---

### Post by QIII on 2012-07-08
When you downloaded the driver an uninstall .sh should have been included.

May I ask if having 12.7 is so important that you would prefer not to use 12.4 in the repo?

It IS the AMD driver version 12.4.  If there is not something earth shattering in 12.7, 12.4 works.

And you are using fglrx, just not the one from the repo.   FGLRX is AMD's terminology.

FireGL for Radeon and X.

---

### Post by Johnny M! on 2012-07-08
Thank You for the Reply [QIII]("http://ubuntuforums.org/member.php?u=628170") !

AMD CCC 12.7 is supposed to be a Great Implementation for the Radeon HD Video Card's  Rendering Capabilities.

I've heard it said that Video Driver Design is sort of like "Voodoo"; a dark magic mixture of software engineering and a little bit of this and a tad of that !

==========================================

But Please Help with This:

Is System - Administration - Hardware Drivers (Jockey?) which shows if the "fglrx" AMD Propritary Driver is Available and if it is Activated; is "fglrx the Driver I downloaded directly from AMD ([http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)) or some other Ubuntu Specific Video Driver from AMD ???

When I run this Command Line in Terminal:
ls /var/lib/dkms/fglrx/
Here is what I get:
8.95  kernel-2.6.32-40-generic-i686  kernel-2.6.32-41-generic-i686

Does this mean I'm using ADM Display Driver version 8.95 or Not ?

Attaching Hardware Drivers Screenshot.

Again all Help for the Uninitiated Appreciated :confused: !

BVR
Johnny M!

---

### Post by QIII on 2012-07-08
The fglrx driver included with Precise is the official AMD/ATI version that was available in April when Precise was released.  There is no "Ubuntu specific" AMD/ATI driver except that AMD/ATI always gives Canonical the April and October versions of the drivers before anyone else gets them.

The open source Radeon driver is not Ubuntu specific.  It is good, but not as feature rich as the AMD/ATI driver.

So, let me rephrase my question:  Do you think that the AMD/ATI driver version 12.7 is such a vast improvement over AMD/ATI driver version 12.4 that you would rather go through the effort of installing from the AMD website when you can install 12.4 from the Ubuntu repository?

And yes, you are using AMD/ATI development branch 8.95.

---

### Post by Johnny M! on 2012-07-08
Hi Again !

AMD CCC 12.7 is not available yet (except in Beta as of 8-July-2012)
So I can't answer your question - until we get some data on frame-rates
for graphical intensive apps (like X-Plane 10) to compare against AMD CCC 12.6, we won't know.  You will probably know sooner and better than me !

Here's what I do know:

- I just (1 hr ago) enabled "fglrx" in Hardware Drivers and after a reboot the system when into a funky low quality graphics mode.

- I restored a Ubuntu Partition Image (with Acronis True Image Home) from 2 hours ago when all was well (with my 10.04 Graphics).    But the system Graphics were still all messed up !

- So I went back to AMD:   [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
and got AMD CCC 12.6. 
Now all is GOOD!   12.6 is A-OK!

But here are a few observations:

- Why is Video Driver Management so Difficult for Linux Novices like myself ?
- Why can't System - Administration - Update Manager just go out and get the latest stable Graphics Driver for whatever Card you're running (AMD or Nvidia) and install it ? 
- Don't get me wrong - I love Ubuntu! :lolflag:   But Video Card Driver Management (user friendly style) is still a work in progress.   And that's a Memo!

BVR
Johnny M !

PS:  AMD CCC 12.6 still going strong !

---

### Post by QIII on 2012-07-08
Video driver management is not difficult if you stick to the version in the repo.

The Ubuntu MOTUs do not rush to include the latest driver because things need to be thoroughly tested before inclusion.

This is different for Windows.  The hardware OEMs spend a great deal of effort and resources to make sure their drivers work with Windows because that is where the money is.  Unless the drivers work, they don't get included in Microsoft's driverbase.  Microsoft does absolutely nothing to make sure Windows works with the driver.  The onus is on the manufacturer.  They make a sound business decision to expend that effort on Windows.

When AMD produces a new Linux driver, you can install it.  But you do not get the benefit of thorough testing for operation.

If you had trouble with the "Additional Drivers" method, you are among those for whom it does not work.  If you look at the wiki in my signature, you will find that this problem is addressed.  I've also included a section about how to enable hardware acceleration, which many mistakenly believe is not available using the Linux driver

---

### Post by Johnny M! on 2012-07-09
Hi to [QIII]("http://ubuntuforums.org/member.php?u=628170") and all out there.

Special thanks to QIII for your patience and tutelage.   I now have a better knowledge and appreciation of how Ubuntu handles Video Drivers.  Please allow me to recap what I think I've learned:

- What Ubuntu refers to as "fglrx" is the proprietary AMD (formerly ATI) Catalyst Device Driver for AMD GPU Video Cards.

- There are three ways of installing (or updating) the fglrx AMD Video Device Driver.   Those methods are nicely summarized at these two web sites:
[http://mrrichard.hubpages.com/hub/2-Ways-to-Install-FGLRX-in-Ubuntu-1110-Oneric](http://mrrichard.hubpages.com/hub/2-Ways-to-Install-FGLRX-in-Ubuntu-1110-Oneric)
[http://www.youtube.com/watch?v=eS9Nmet_sqQ](http://www.youtube.com/watch?v=eS9Nmet_sqQ)
I was having the best luck by downloading directly from AMD  [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
and running the Installation Executable in Terminal.   
For some reason, my Synaptic Package Manger was only pulling down a much older AMD Driver version (8.723) and my system seemed to operating in a Low Quality Graphics Mode (if I tried updating fglrx thru Package Manager) ??

- You should remove the old AMD fglrx driver in "Hardware Drivers" before installing an updated version (with a system reboot between all major administrative actions).   Funny - Sometimes 'Hardware Drivers' will not show me any proprietary drivers (fglrx) even though I can see them (on my system) in Terminal with this command:  ls /var/lib/dkms/fglrx/

After much trial and (many) error - I was able to arrive at either one of the following two Graphic Configurations (Please see Attached Screenshots):

- fglrx 8.723 installed via Pacakge Manager
or
- AMD Catalyst 12-6 (Driver 8.98 installed via Direct Download and executed in Terminal (see Screenshot).

Again - Thank you for your Ubuntu Mentor-ship !

BVR
Johnny M!

PS:  I'll keep an eye out for 12-7 !

---

### Post by QIII on 2012-07-09
If you are using Jaunty, that version is quite old, beyond its end of life.

The newer version of fglrx is not included because that version is no longer receiving updates.

---


---
title: "Dell Inspiron 4010 Brightness Control"
date: 2010-06-07
forum: Hardware
---

### Post by rajayoganand on 2010-06-07
Hi,

I have a dell New Inspiron R 4010 Laptop.Which came with pre-installed Windows Home Premium 7. I have removed all partitions from hard disk and installed my favorite OS..Ubuntu 10.04 LTS 64 Bit. After installing few things I stuck up

1. NIC
2. Wi-Fi
3. Brightness control
4. Headphone Jack

1 and 2 I was able to solve by installing specified network drivers from the vendor web site and help from the community. I love Linux because its powered by the well wishers the great community support.

I have installed new kernel as part of solving the problem 3 and 4. 
New kernel 2.6.35-020635rc1-generic is supporting my headphone jack.. Thanks.

But brightness control is not working but its showing on the screen (at least)

I am able to control the brightness from GRUB menu.

I am back to the original kernel came with 10.04 LTS  vmlinuz-2.6.32-21-generic because there is a display vibration i new kernel.

I would appreciate any support from the community to solve this issue. 

Please post me back for any more info required to solve this issue.

Thanks a lot for all members and readers.
Thanks a lot to the kernel team.
Thanks a lot to Ubuntu team.
Thanks a lot Linux.

raj

---

### Post by wilee-nilee on 2010-06-07
Does holding down the fn key and using the < > arrow keys work, not the symbols but the 4 keys that are right-left. Up and down should control the volume. Maybe different on your computer.

---

### Post by Onesimus on 2010-06-07
There is a brightness applet that you can add to the top panel.  I find this was a work around - without too much effort.

---

### Post by 3rag0n on 2010-07-03
> **rajayoganand said:**
> Hi,

But brightness control is not working but its showing on the screen (at least)

I am able to control the brightness from GRUB menu.
raj

Hi. My new laptop is of the same model. Thanks for letting me know that the issues 1+2+4 are solved.

I have the brightness issue too. Changing the brightness using the Fn+ F4/F5 keys doesn't work. (Doing that, the notifier shows a brightness bubble on the top-right, but it doesn't change).

The applet also doesn't work.

Since this is a new model, I suspect more people will buy it and post here. I'd like to know if someone found a solution. Please suggest one if you think you can help!

Thanks.

---

### Post by humm on 2010-07-24
I own a Dell Inspiron N4010, I am too facing the same brightness problem.

Can someone please help?

---

### Post by crabiorc on 2010-07-26
Do anyone have an update on this?
My kernel version on the Inspiron N4010 is 2.6.32. The wired ethernet is working fine after the workaround of installing compat-wireless modules. I am yet to make my wireless work :(
Now found from this post and confirmed that the following is not working
-Headphone jack
-Microphone (Builtin and Mic jack)
-Brightness increase/decrease keys
-Touchpad disable key
-External display swap key
I hope we can have this thread on fixing all these :(

The brightness applet is of no use. And when the disable touchpad key is pressed, i see a notification. But still the touchpad works.

---

### Post by waseemf on 2010-07-28
> **crabiorc said:**
> Do anyone have an update on this?
My kernel version on the Inspiron N4010 is 2.6.32. The wired ethernet is working fine after the workaround of installing compat-wireless modules. I am yet to make my wireless work :(
Now found from this post and confirmed that the following is not working
-Headphone jack
-Microphone (Builtin and Mic jack)
-Brightness increase/decrease keys
-Touchpad disable key
-External display swap key
I hope we can have this thread on fixing all these :(

The brightness applet is of no use. And when the disable touchpad key is pressed, i see a notification. But still the touchpad works.


I also have the same model and I m also facing these issues. The touchpad, brightness key. But my microphone is working fine. You need to go to sound preferences after clicking on volume icon, click the input tab and check whether the microphone volume is UP & mute is not checked.

Hope that will work for u as well.

And hope we get a solution to the brightness key & touchpad problem soon!

---

### Post by crabiorc on 2010-08-02
Hi Waseem
My Dell Ins N4010 has Ubuntu 10.04 with Kernel 2.6.32-generic now
The issues i have currently are
-Brightness, Disable touchpad keys are not working (Found no solution yet)
-Speakers and Mic are working
-Headphone jack is not working (No sound connecting a headset)
-Bluetooth and WiFi are working
-Ethernet is not working (Found the below solution to enable ethernet card)
Install the updated stable version of 2.6.43 kernel from
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

---

### Post by mandol on 2010-08-03
Hi,

I own an N4010 as well. No go on the touchpad so far.

However, I have sorted out the headphone jack issue,

You need to follow the instructions [here]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") (download and install the script)

Also, very important. This did not work for me without a fresh install. You need to reinstall ubuntu and then download and install the script.

I didn't have any brightness issues, but I'm not on Ubuntu, I'm on Kubuntu, maybe that's the reason.

Touchpad config anyone?

Regards,

Kartik Krishnan

---

### Post by nadeepa on 2010-08-21
Same model, same problem. Network, WiFi & Headphone have some workarounds. But still haven't find one for brightness control.
Touchpad control works fine.

I'm using Lucid with 2.6.32-24-generic kernel.

---

### Post by psynaps3 on 2010-08-22
Has anyone got a solution for the brightness issue? Is there any way that we can permanently set the brightness level?

---

### Post by psynaps3 on 2010-08-22
All, [bug 568611]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/568611") is open for this issue.

You can find a patched kernel by Kamal which works perfectly for Inspiron 14R. Add the PPA, install, and reboot.

---

### Post by mike909 on 2010-08-29
fyi the alsa script pointed out breaks the mic input.
inspiron n4010:

lshw -C Sound
  *-multimedia            
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
Now I need to work on getting the MIC working again, as it was with stock alsa version (.21)

---

### Post by mike909 on 2010-08-31
> **mandol said:**
> 
However, I have sorted out the headphone jack issue,

You need to follow the instructions [here]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") (download and install the script)

Can you verify for me that your mic still works? (not the mic input, the external mic...ie web-cam mic)

---

### Post by mike909 on 2010-08-31
> **psynaps3 said:**
> All, [bug 568611]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/568611") is open for this issue.

You can find a patched kernel by Kamal which works perfectly for Inspiron 14R. Add the PPA, install, and reboot.
I don't think this applies to 2.6.32-24-generic. If it does, can someone tell me the exact command? I've added the ppa but apt-cache search kamal returns nothing. What's the name of the package to install?

---

### Post by mike909 on 2010-09-01
Instead of the alsascript, I followed this and it worked:
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
I am yet to figure out how to fix the suspend or brightness control issue, as there doesn't appear to be a patched kernel for 2.6.32-24, and if I used an older kernel, I have other problems (sound fails again).
I can get brightness & resume fixed, but I can't get EVERYTHING fixed in one kernel (ie both network interfaces, headphone jack, brightness & resume). Closest I can get is all fixed but brightness & resume.

---

### Post by muhammadwaqas on 2010-09-12
Hi, (Three things are working now on my laptop using following information. i thought to share it.)
I Got **dell inspiron n4010** (14r) and **ubuntu 10.0.4** **64bit**

I installed first wired lan. (downloaded the driver from other computer and using pen drive shifted to my laptop. )
Then i installed wireless.

I followed instructions from below url for these two things.

1. NIC (wired lan)
2. Wi-Fi (wireless)
[http://ubuntuforums.org/showthread.php?p=9817325#post9817325](http://ubuntuforums.org/showthread.php?p=9817325#post9817325)

========= brightness control=========

3. Brightness control
[http://kernel.ubuntu.com/~kamal/i915_brightness/latest-lucid/]("http://kernel.ubuntu.com/%7Ekamal/i915_brightness/latest-lucid/") (download and install all three deb files)
"as u know deb files can be installed directly in ubuntu"
Restart.

turn on  with 2.6.32-23-generic kernel. *(select 2.6.32-23-generic at start if you have other kernels too.)

now my wired, wireless and brightness control are working. 
Thanks to ubuntu. i love it.

---

### Post by muhammadwaqas on 2010-09-12
> **mike909 said:**
> I don't think this applies to 2.6.32-24-generic. If it does, can someone tell me the exact command? I've added the ppa but apt-cache search kamal returns nothing. What's the name of the package to install?


Brightness control
[http://kernel.ubuntu.com/~kamal/i915_brightness/latest-lucid/]("http://kernel.ubuntu.com/%7Ekamal/i915_brightness/latest-lucid/") (download and install all three deb files)
"as u know deb files can be installed directly in ubuntu"
Restart.

turn on  with 2.6.32-23-generic kernel. *(select 2.6.32-23-generic at start if you have other kernels too.)

---

### Post by waffleez_89 on 2010-10-19
does suspend and mic stil not work? 

i currently have Super Os 10.10 and everything works except for brightness control and i am wondering is there a fix for this that wont break my other stuff

---

### Post by andl36 on 2010-10-20
Can anyone report if the brightness control issue has been fixed in 10.10?

---

### Post by brkearns on 2010-10-20
The brightness control is not yet fixed in the mainline 10.10 kernel.  However, there is a PPA to address this situation.  The PPA can be found here for the 10.10 Maverick release.

[https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)

For those who are having touchpad issues, mine were pretty much fixed with the Maverick release.  I added the atkbd.reset parameter to the Grub configuration to address the suspend issue, but that was all I needed to do.

---

### Post by waffleez_89 on 2010-10-21
i know this is going to sound newbish but how do i add that ppa?

also what did you do to get suspend working?

---

### Post by waffleez_89 on 2010-10-28
thanks for the help guys  *sarcasm intended* i got the ppa working by doing this 

sudo apt-get-repository ppa:kamalmostafa/linux-kamal-mjgbacklight

the kernel works great with brightness but suspend still wont work.

---

### Post by brkearns on 2010-10-31
OK - here are the steps to fix the suspend issue. This is assuming that the problem you are experiencing is that the mouse or keyboard will not awake the computer from suspend when you open the lid.

Open a terminal session

type sudo gedit /etc/default/grub

Look for the line that says:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Change that line to read
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash atkbd.reset"

Save the file and close the editor window.
Next you have to update your grub loader

in a terminal window type the following:
sudo update-grub

This should rebuild your menu.lst file -- the file Grub uses at boot to add the atkbd.reset parameter to the kernel.

Reboot your machine.  You should now have a functional suspend - resume capability.

Sorry if I was too brief in my earlier posts on these issues.

---

### Post by brkearns on 2010-10-31
As for installing PPA's, the guidance is really in the link I posted earlier.  Specifically, it reads:

**Adding this PPA to your system**

                            You can update your system with unsupported packages from           this untrusted PPA by adding **ppa:kamalmostafa/linux-kamal-mjgbacklight**           to your system's Software Sources.           ([Read about installing]("https://launchpad.net/+help/soyuz/ppa-sources-list.html")) 



You can do this by doing the command line methods in the Read About Installing link.  Or you can add the Software Sources through the Synaptics Package Manager (Settings->Repositories). 



 I choose to add PPAs through the Synaptics Package Manager.  In this case, I added two repositories, one for the binary kernel images in the PPA and one for the source files in the PPA. 



First, the binary kernal images.  From the Software Sources window, choose the "Other Software" tab. Select the Add button, and choose the type of Binary.  Enter in the following URI:
[http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu](http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu)
Then enter maverick for the distribution and main for the components.
 

For the source files, repeat the process again, but choose the Source type.  

The URI, distribution and component options should be the same as listed above for the binary option.  Now if you do an update, you should see the modified kernels provided by this PPA.

---

### Post by brkearns on 2010-11-01
Please note that the updated Maverick kernels are out and the default behavior is for Maverick systems to update to the new mainline kernel released by the Ubuntu kernel team.  This 2.6.35.23 kernel is seen as an upgrade from the PPA kernel that addresses the brightness issue.

IF YOU PROCEED WITH THE UPDATE OF THE linux-image-2.6.35.23 KERNEL, THE PPA WILL NO LONGER BE VALID AS THEY BOTH SHARE THE SAME RELEASE NUMBER.  If you do it by accident, you can use the FORCE VERSION capability in Synaptics Package Manager to force the use of the PPA instead of the mainline release. :cool:

---

### Post by waffleez_89 on 2010-11-16
there has to be an easier way to apply this ppa. everytime i do a fresh install i have to hunt for thr linux file and it keeps telling me i have broken packages...

---

### Post by bjornd on 2010-11-17
Same problem with brightness on a Dell Inspiron 17R (N7010). F4+F5 makes the display brightness notification show on screen, but brightness doesn't change. 

Bonus: I bought the laptop without OS :)

---

### Post by supranov on 2011-07-21
Thanks to brkearns, for your infos.
brightness control works at N4010 with Ubuntu 11.04, now i don't need black sunglasses when work with this Dell.
:D

---

### Post by Seymour.Birkoff on 2011-08-17
Well, this post is 4 years old with no solution yet. I have the same problem.

---

### Post by 405jayb on 2011-08-26
Hope this works for some. I Got my brightness keys working only with this solution. Install xcalib from the repositories and run this command.. xcalib -co -90 -a .To set it back to default (100) xcalib -c. I just set those as my keyboard shortcuts.

---

### Post by 405jayb on 2011-08-26
By the way, this was done on a dell inspiron n7010.

---


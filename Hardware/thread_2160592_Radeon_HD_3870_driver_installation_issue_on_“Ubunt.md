---
title: "Radeon HD 3870 driver installation issue on “Ubuntu 12.04 precise”"
date: 2013-07-07
forum: Hardware
---

### Post by Miki800 on 2013-07-07
Radeon HD 3870 driver installation issue on "Ubuntu 12.04 precise":
[EDIT](TLDR)
Hey everyone, I got my problem fixed by using the latest answer given to me here:

[http://askubuntu.com/questions/316490/fixed-radeon-hd-3870-driver-installation-issue-on-ubuntu-12-04-precise](http://askubuntu.com/questions/316490/fixed-radeon-hd-3870-driver-installation-issue-on-ubuntu-12-04-precise)

used the makson96/fglrx repository method and it worked like a charm!

The given Instructions I used can be found in here:
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)
for prettier formatting look'em up at the bottom of the page of the first link! ^_^
yay!
[/EDIT]

I know that this is my actual driver because:

> ~$ lspci | grep -i amd
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV670 [**Radeon HD 3870**]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV670/680 HDMI Audio [Radeon HD 3690/3800 Series]


Steps I've taken:

1. Gone here:
[http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)

2. Installed "AMD Catalyst™ 13.1 Proprietary Linux x86 Display Driver"

3. Restarted

4. Launched "amdcccle" and got the following error message:

_**"Initialization error"**_

> There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
No AMD graphics driver is installed, or the AMD driver is not functioning properly.
Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.

-5. Got my hands on something called: "ubuntu-amd-catalyst-install", installed and and launched it and it showed me the following error message:

**_"The Fan Club - Ubuntu AMD Catalyst™ Install"_**
> Detected graphics controller:
 
 Hynix Semiconductor (Hyundai Electronics)  Radeon HD 3870
 
 Ubuntu 12.04 
 Linux Kernel: 3.5
 X-Server version: 
 
 
 Your system is not supported by this driver



[SIZE=4][FONT=Arial Black]**_[COLOR=#FF0000]Your system is not supported by this driver <--- ????[/COLOR]_**[/FONT][/SIZE]




I installed synaptic and then installed the fglrx driver from there, didn't make "amdcccle" start working either.

I've also ran "aticonfig --initial" and it didn't change anything.


At the moment I am not pleased because my maximum (and only) resolution is 1024x768 and I wish to change that.


I definitely remembering installing Ubuntu couple of years ago with the same hardware never got this kind of error message.

Have the ubuntu development team done something wrong over the years to ubuntu
that degraded it's ability to support my (unchanged) hardware?

I've looked up the suggested searches and non of them seem to help me, I put my trust in your hands, I hope that you can help me figure out why ubuntu has stopped supporting my used-to-be-completely-supported graphic card.




Thanks ahead for any positive helpers.


I was told to remove everything I've done (which I have by now) and to go here and use this guide:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I did, then in step 2.1.8 I got this output after sending the command "fglrxinfo":

> X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

when it is written in the guide that I should get something like:

> display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6300M Series
OpenGL version string: 4.2.11733 Compatibility Profile Context


Please ubuntu experts I need your help, why is this happening? what do I do?


I also tried posting this help request in other domains but they are too slow, so I thought of trying out my luck in here as well.

---

### Post by Bashing-om on 2013-07-07
Miki800; Hi !

May not be much that can be done. It is unfortunate that such popular cards no longer have support from AMD (ATI):
> 

IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)

So, lets see what kernel you are running:
```
uname -r
```
3.5 series and above kernel and the only option for a graphics driver is the open source drivers.

[INDENT][INDENT]a tale is told
[/INDENT][/INDENT]

---

### Post by Miki800 on 2013-07-07
3.5.0-36-generic

I had this very same hardware and an older ubuntu with full graphic card support some time ago, I think maybe even before 04/2012.

my point is - code of drivers that support what I got for ubuntu - exists (or at least existed and then removed maybe.. ?)

do I need to downgrade my kernel version or ubuntu version itself to make that code work again?

---

### Post by Bashing-om on 2013-07-07
Miki800;

One may down grade the kernel .. but that is not at all a recommendation... -one has to really know their system and stay on top of it- there are a number of risk involved in doing so.

Consider this... (re-)install the older version 12.04 as it has the kernel that is compatible with ATI's proprietary drivers.
I am also in your boat with the older ATI graphics card and I have kept the 2.6 kernel line on my system rather than upgrading to kernel 3.5 (12.04.2).
Then you will maintain full support and no security risk///the 2.6 kernel series remains valid for all updates within the initial install.
Downside: there will be a ton of updates to get the install up to date !

It will take a bit of research to find that old 12.04.1 install image, but I know it is available.

[INDENT][INDENT]ubuntu, there are options[/INDENT][/INDENT]

---

### Post by Miki800 on 2013-07-07
> **Bashing-om said:**
> Miki800;

One may down grade the kernel .. but that is not at all a recommendation... -one has to really know their system and stay on top of it- there are a number of risk involved in doing so.

Consider this... (re-)install the older version 12.04 as it has the kernel that is compatible with ATI's proprietary drivers.

sorry I am not following, are there more then just one 12.04 download version from ubuntu.com?
because I downloaded the one I found for 32 bit.

Also when I said before that in the past I had ubuntu working with this graphic card I meant before 01/04/2012, there was no "old 12.04 version" back then because 12.04 did not exist yet.

> **Bashing-om said:**
> 
I am also in your boat with the older ATI graphics card




> **Bashing-om said:**
> 
and I have kept the 2.6 kernel line on my system rather than upgrading to kernel 3.5 (12.04.2).
Then you will maintain full support and no security risk///the 2.6 kernel series remains valid for all updates within the initial install.
Downside: there will be a ton of updates to get the install up to date !

oh crap, now I get it -_-...

> **Bashing-om said:**
> 
It will take a bit of research to find that old 12.04.1 install image, but I know it is available.
[INDENT][INDENT]ubuntu, there are options[/INDENT]
[/INDENT]

oh sh*t,


I found some old 12.04 image after downloading the current one I used for installation and thought
what the heck, duplicates? better delete that old one for taking space O_O

---

### Post by Bashing-om on 2013-07-07
Miki800;

If You do not mind (re-)installing ... lemme see what I can find,, I am sure the 12.04.1 version is still available.

[INDENT][INDENT]laughing while trying to help
[/INDENT][/INDENT]

---

### Post by Miki800 on 2013-07-07
Hey everyone, I got my problem fixed by using the latest answer given to me here:

[http://askubuntu.com/questions/316490/fixed-radeon-hd-3870-driver-installation-issue-on-ubuntu-12-04-precise](http://askubuntu.com/questions/316490/fixed-radeon-hd-3870-driver-installation-issue-on-ubuntu-12-04-precise)

used the makson96/fglrx repository method and it worked like a charm!


The given Instructions I used can be found in here:
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)
for prettier formatting look'em up at the bottom of the page of the first link! ^_^
yay!


Thank you all for attempting to help so far, I appreciate it very much!

---

### Post by Bashing-om on 2013-07-07
Miki800; Hey Indeed Great news !

Progress made in order to keep Good graphics cards operable.
also corrections to my kernel version in 12.04.1 ... should be read as 3.2 series.. not 2.6 as stated... sheeshh ... whatever was I thinking ?

Good news and glad you passed it along ...

[INDENT][INDENT]take care, enjoy[/INDENT][/INDENT]

---

### Post by Miki800 on 2013-07-08
Thank you, only remaining issue now is that I am having some uncritical difficulties setting up clone display with a certain resolution that was enabled under windows.
the currently max supported resolution for tv+screen cloning is stretched in a very violent way to my eyes, so I set both to as similar as possible of a resolution and they are on top eachother
(1700x1000, 1680x1050) which gives me some headaches dealing with.. but I guess its not a big deal for now.

I remember having this problem every time I go back to linux, don't remember if I ever got to solving it in my past attempt.

before I give up linux again I think that I might backup my important /etc/bla/*.cfg files in my dropbox for the next attempt :P
world didn't have dropbox last time I tried

---

### Post by Bashing-om on 2013-07-08
Miki800; Hi !

I do not use dual monitors.. so not much help in that respect... however, lubuntu may have the more user friendly setup for dual monitors from what I have passingly observed. Just bear in mind there are limitations to what the combined resolutions of the monitors that the graphics card can drive.

cheers

---

### Post by QIII on 2013-07-08
Please use images only when necessary to illustrate a problem encountered.

When you do use images, use the attachment functionality (the paper clip above the text box) to add a thumbnail.

Large images are a distraction and are difficult for those with low bandwidth or data restrictions to view.

Thanks.

---

### Post by Mark Phelps on 2013-07-08
> The given Instructions I used can be found in here:
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

If you read through this, you will see that part of the changes required downgrading your X-server to an old version.

This is very likely to cause serious complications down the road as other updates come through.

You are trading a short-term improvements for serious long-term risks of system damage.

---

### Post by Miki800 on 2013-07-08
> **Mark Phelps said:**
> If you read through this, you will see that part of the changes required downgrading your X-server to an old version.

This is very likely to cause serious complications down the road as other updates come through.

You are trading a short-term improvements for serious long-term risks of system damage.

You could look at this that way, or one could look at that the other way and say:
[QUOTE=Parallel universe]Hello Xorg developers
if you look carefully at your version upgrades, you will see that parts of the changes do not play well with the latest version ati legacy drivers available, both the open source and the official AMD release.

This is very likely to cause serious complications for potential users down the road as nobody will modify these old drivers to be once again compatible with your changes.

You are trading a certain percentage of your potential users who have this hardware, for an upgrade fashioned in a way that throws a punch in the face of the legacy drivers.[/QUOTE]
no offence intended, just some sarcasm-steam of this whole situation, by I'm not emotional, I'm just really happy that I'm past this and it works :)
[SIZE=1]plus I had to throw in some humor after the memes were destroyed :([/SIZE]


anyway now seriously, for me its not something as meaningless as only a short-term improvement,
without these drivers working my whole desktop experience felt incredibly heavy and slow,
nothing that needed OPENGL could work.

Now I can use parallel monitors with a good resolution, I can run StarCraft II and Diablo III and google-earth and much more and they all work very smooth.
Which is a huge improvement compared to the last time I installed Ubuntu.

If it (the drivers and the downgraded system) worked back then when they just got released it might work now,
and if it will damage my graphic card and melt it down then it would be a great opportunity to buy a newer one :)

---

### Post by Bashing-om on 2013-07-08
Miki800; Hey.

I am playing catch up in response to the adverse affects my actions have resulted in.
See also this thread.
[http://ubuntuforums.org/showthread.php?t=2160054&p=12722137#post12722137](http://ubuntuforums.org/showthread.php?t=2160054&p=12722137#post12722137)

[INDENT]thoughtless conduct[/INDENT]

---

### Post by Miki800 on 2013-07-08
> **Bashing-om said:**
> Miki800; Hey.

I am playing catch up in response to the adverse affects my actions have resulted in.
See also this thread.
[http://ubuntuforums.org/showthread.php?t=2160054&p=12722137#post12722137](http://ubuntuforums.org/showthread.php?t=2160054&p=12722137#post12722137)

[INDENT]thoughtless conduct[/INDENT]

I see.. well I would take full responsibility for my actions and not blame anyone else
if the day would come after this current stable state I'm at
the day in which my system would explode! or something less drastic too..

I just have this feeling that the chance that something bad will happen is not very high.

---

### Post by Bashing-om on 2013-07-08
Miki800;

Good deal all... I rest assured in your knowledge and abilities.

Take care and I will read you next time.

[INDENT]all's well that ends well[/INDENT]

---


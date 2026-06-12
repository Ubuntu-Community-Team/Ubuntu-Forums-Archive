---
title: "Bugfixing the eeepc for Lucid"
date: 2010-04-30
forum: Hardware
---

### Post by bornagainpenguin on 2010-04-30
[img]http://img408.imageshack.us/img408/3721/wallbanger.jpg[/img]
...because it feels so good when I stop...

This time you can play along at home!

[IMG]http://img695.imageshack.us/img695/9885/bang20head20here.th.jpg[/IMG]

Click thumbnail for larger version of the stress reduction kit which can be used over and over again!

This is **Bugfixing and Working Around Ubuntu 10.4 LTS Lucid Lynx Guide** v.004

Now with 90% more sarcasm!  If you act now we'll double your bitterness!  But wait there's more!  I can't stop using exclamation marks!!!1111

I've begun to think Linus' law ("given enough eyeballs, all bugs are shallow") is like Godwin's Law--it doesn't work when invoked directly.  I'm sorry, my bad.

Lucid reinstalls now totaling 00399, but who's counting?  Things I have learned so far...

The default kernel will not consistently give eeepc users a wifi signal.  Sometimes it is possible to get a short lived connection by toggling the WiFi on and off, but you *will* need a wired connection to update and fix your Lucid install.  Once you get your system updated to the latest default kernel this actually gets worse ninety nine percent of the time.

Powermanagement is still broken and there are strange run away processes that hide in the background and ramp up your processor usage.  For some reason this mysteriously goes away or stops happening so frequently after a few days time.  I don't know why.  At first it was thought that UbuntuOne was the culprit, or that the kernel had an issue with the ext4 filesystem, but although removing UbuntuOne and changing to a different filesystem seemed to have helped some neither really fixed things a hundred percent.

How Lucid Lynx was allowed out the door with these and so many other bugs is beyond me.

Before proceeding I should warn you that I am *not* an expert and that many if not all of the tips and tweaks that follow are "dirty hacks"  which could cause your eeepc to spontaneously turn into yogurt, make your significant other start chasing after moving vehicles in the street, cause your vision to go dim, etc etc etc.  Proceed with caution.  I am not responsible if things go awry.  I will try to credit the sources of my information when at all possible, but no guarantees.

NOTE: I am performing all these operations using the EeePC 901 2103 BIOS with SLIC and a changed OEM image.  Using a different bios will have different results in some cases.  Your mileage may vary.

**Installing Ubuntu...**

**Speed up your Lucid Lynx (re)installs**

There are several things you can do to help speed along the process of doing your Ubuntu (re)installs.

*Do not connect to the internet during install time*

Do not connect to the WiFi or the Ethernet during install and you won't sit there for an additional hour staring at the screen while the overloaded default servers download unneeded language packs.

I've seen install times drop down to almost nothing just by not connecting.  If Canonical wants to install language packs it can include them on the ISOs, and not waste our time downloading them during installation.  'Almost done installing' my ***...

*Backup your debs*

When planning on doing a reinstall of Ubuntu make it a practice to navigate to the apt directory and copy all the *.debs over to a flash drive or SD card before doing the install.  Believe it or not but there are now over five hundred megabytes of updates to do after Ubuntu is installed.  If you back up the previous updates you've done you'll be able to apply many of them without having to wait for them to download again.  This can shave off hours depending on your download speeds!

Where you want to go is:

```
/var/cache/apt/archives
```
Select all the files (minus the one named lock) and copy them to a safe place on an external drive.

Once you have Ubuntu installed you can copy them back by opening the terminal and getting a root nautilus session::

```
sudo nautilus
```
Now copy your backed up .debs from your portable drive back to the archives directory path listed above.  Now once you connect to the internet and run update manager, you won't have as many files to download from the internet.

Technically the above is really more for post installation, but I've moved it up so that people don't blow away their previous installs and *then* wish they'd saved their debs.

**The file system**

Previously I recommended *not* to install using ext4 because there is a kernel process that is calling constantly and needing to check the disk if you do and will be one of many many processes that will screw up your power management.  This issue seems to be fixed in the recommended kernel I list below.  You can still read about the issue people were having on the [ArchLinux Forums](http://bbs.archlinux.org/viewtopic.php?pid=715998), home to **tons** of good information for eeepc owners.  In particular, user lagagnon explains the issue as follows:

> **lagagnon]More info: using "iotop" the culprit appears to be "jbd2/sda1-8", which appears to be a kernel process associated with journaling on the ext4 filesystem, if my googling around is correct. And yes it is an Atom processor here also. Strange, guess will just have to wait and see if future updates fixes it. Does not seem correct that it has to access the disc so often.[/quote]
Just for fun it appears this issue did not get seem to be fixable by **noatime** so simply disabling journaling was *not* a fix.  The only fix appeared to be in not using ext4.  So we had to ask ourselves whether the speed in boot times is worth the random processor overruns, the overheating that seems to result, and the inability to use many commercial backup imaging programs?  Thankfully this no longer seems to be an issue and the trade offs are no longer necessary if you use the kernel recommended further down below.

Still, there are some [situations](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Performance%20regressions%20with%20ext4%20under%20certain%20workloads) where ext3 is better in Lucid than ext4, so you'll have to do some homework.  I do *not* recommend reiserfs, because you will find yourself doing disk checks nearly every other day and it is an unsupported filesystem with a very limited future.

**Update!**

User Ceno reports that there is a way to use ext4 *and* disable journaling thus fixing the jbd2/sda1-8 bug, but it is a bit involved, so your mileage may vary!  Personally I intend to stick with the kernel mentioned above and explained below, but for those who might be interested, here is that fixed:

[quote=Ceno]Regarding the jbd2/sda1-8 "bug", if you will, mentioned in the File System section of the 1st post, disabling journaling does indeed solve it.
First thing's first, we can confirm that our ext4 partition is running a journal with

```
$sudo dumpe2fs /dev/sdaX | grep has_journal
```
Disabling journaling is rather easy, the only drag is that to make structural changes to a filesystem, the filesystem cannot be mounted with read/write privileges. So, run a live cd and hit

```
$sudo tune2fs -O ^has_journal /dev/sdaX
```
And it's done. Now when you boot, the change will be noted and the disk will be checked for errors. When the system is finally up we can run this again to confirm that in fact ext4 is running without a journal

```
$sudo dumpe2fs /dev/sdaX | grep has_journal
```
should now return nothing.

With this quick fix, no more constant IO peaks. I can now watch youtube videos without constant freezes.[/quote]
Thanks for sharing this with us!

**Partitioning**

Everyone has their own preferences on this, but this is what I do:

4GB SSD
/---/4GBs
---/efi 8mbs

16GB
/----swap 1GB
/-------/usr/share 4GB
/---------data 11GB

I find that my system slows down dramatically when I partition the 16GB SSD (the slower one) as my /home so what I do now is partition /usr/share on the slower SSD and that not only saves me some space for applications it also frees up space for those configuration files and themes in /home.  I get around the limitations of the User Folders for media (Music, Videos, Public, etc) with symbolic links.

I will continue to add more preinstall tips as they become available, so please feel free to share any you come across that you know work!

**After the installation...**

You now have Ubuntu Lucid Lynx installed&#8212 said:**
> Try this, as root: [sudo su]

```
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash

update-initramfs -u
```
That should make plymouth appear. But, it might delay your boot a tad-bit.
Considering how fast things can boot on our eeepcs already I don't think we'll miss the few seconds it takes, and at least now we know that the system is booting!  You'll need to reboot to see the changes take effect.

**Reduce writes to your SSDs**

These used to be tips that fell under the category of stuff "everyone knows" but as new people come in and the information gets bitrots as wikis get ignored in favor of forum posts (like this one,) people forget.  So here they are all in one place because not everyone does know about these and because I notice a major reduction in heat with them enabled and a major speed up in Firefox using them.

From the [EasyPeasy Wiki](http://wiki.geteasypeasy.com/How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive) and [Fedora-netbook HOWTO](http://www.fedora-netbook.com/index.php?p=1_21):

```
sudo gedit /etc/fstab
```
For each of your partitions (/, /usr/share, /data) add ",noatime" after "defaults".

For example (from desktop, not eeepc do not copy exactly):

```
# / was on /dev/sda1 during installation
UUID=6079da5f-faef-4c8a-b5c1-2685cd47fa8a /               ext3    noatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=51a9de0a-fdfc-47f7-a96e-9b705edd2e8f /home           ext3    defaults,noatime        0       2
```
Then add the following to the end of the file:

```
# reduce the number of writes
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/tmp tmpfs defaults,noatime,mode=1777 0 0
```
Save the file and close the editor.

Now let's do something about the swap!

```
sudo gedit /etc/sysctl.conf
```
Scroll down to the end of the file and copy the following:

```
#
# reduces the likelihood of the system using the swap partition as swap
vm.swappiness = 1
vm.vfs_cache_pressure = 50
```
Save this and close the editor.  Now open Firefox.

In the URL bar enter the following and type enter:

```
about:config
```
Ignore the warning about voiding your warranty and hit the button with the text "I'll be careful, I promise!"

Right click and select New --> String --> Paste the following:

```
browser.cache.disk.parent_directory
```
as the name and as the string value type in:

```
/tmp
```
This will instead store the cache in RAM if you created the tmpfs entries in fstab as described above.  You *did* didn't you?  Other wise skip this last step altogether as it will slow down your browser!  Only do this step if you've aded tmpfs to your fstab!

Now save the file close the editor and go on to the next step.  Settings won't take effect until rebooting.


**The broken theme support:**

Some people like the new themes, because finally they're getting the dark themes they've always wanted in workable fashion!  Except, the themes have this sense of being unfinished about them for some strange reason...

```
http://img594.imageshack.us/i/mailnotificationtray.png/

http://img807.imageshack.us/i/vlc2.png/
```

I couldn't imagine why it looks unfinished!  Seriously, does this look finished to *you*?  Unfortunately there's nothing we can do about it, since as far as Canonical is concerned everyone else needs to fix their programs to accommodate Ubuntu...what was that about [tribalism](http://www.markshuttleworth.com/archives/439) again Mark?

Of course these issues are no big deal right?  It's only a few apps that break this way, right?  [Not so much...](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/403135?comments=all)

Obviously Ubuntu is perfect and all 337 people who took the time to join Launchpad and report this bug (not to mention **how *many* duplicates** are all nuts.  Oh and pointing out these facts and the way so many bugs are being ignored so Shuttleworth can play retro skin designer is "[pointless bashing](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/403135/comments/160)"  and totally not a reflection of anger at seeing bugs ignored for so long...

Then again this is the same guy who thinks that 'windicators' are a good idea, so I guess some stupidity is to be expected.

Hey Mark, here's a clue&#8212;this type of thing was tried by almost everyone back in the early days of GUI skinning and there's a reason why it didn't make it as a default theme *anywhere*, and that's because it sucks as a work environment!  But hey if you really want to go back to 1998, it's your dime...

[img]http://img831.imageshack.us/img831/299/iconomiser.png[/img]

[img]http://img148.imageshack.us/img148/8536/idioth.png[/img]

**Those $#&% buttons...**

If by this point you've found yourself suffering from disorientation due to muscle memory constantly having you mouse to the wrong location for the window buttons, maybe this would be a good time to change them back to the defaults?

In terminal:

```
gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close
```
You could also just get [Ubuntu-Tweak](http://blog.ubuntu-tweak.com/downloads) and move them around to your heart's content...  

Personally after some time I've gotten used to the window controls being on the left and use the "[Black Fruit](http://gnome-look.org/content/show.php/Black+Fruit+-+like+OSX,+but+darker?content=118954)" emerald theme because it complements the default theme so well.  Your mileage may vary.

**Make the default themes more compact...**

Okay, you've rebooted and hopefully everything has gone smoothly and you've logged into your desktop without issue.  You should be seeing the new Ambiance and Radiance themes...  Unfortunately these new themes are slightly larger than any of us would like to see on the small screens of our eepcs.  Elwood, a blogger [has a tip for us](http://aarcudi.netsons.org/blog/?p=258) to make the theme look a bit more compact:

> **Elwood]Just add this line to the theme&#8217 said:**
> 
Personally I find that I like my icons smaller than this on my eeepc, so I've amended that slightly by copying the sizes from one of the older HumanCompact themes to this:

```
gtk-icon-sizes = "panel-menu=16,16 : gtk-menu=16,16 : gtk-button=16,16 : gtk-small-toolbar=16,16 : gtk-large-toolbar=16,16 : gtk-dialog=32,32 : gtk-dnd=32,32"
```
You'll need to run sudo when you open the gtkrc:

**Ambiance:**
```
sudo gedit /usr/share/themes/Ambiance/gtk-2.0/gtkrc
```
**Radiance:**
```
sudo gedit /usr/share/themes/Radiance/gtk-2.0/gtkrc
```
Find the line that says:

```
gtk-icon-sizes = "panel-menu=22,22:gtk-button=16,16"
```
change the line so it reads to:
```
# gtk-icon-sizes = "panel-menu=22,22:gtk-button=16,16"
```
and paste the above lines directly under the now blocked off lines of text.  Save the theme and reboot to refresh the system and reload gnome-settings-daemon.

If the above seems too daunting you could also try just downloading the "AmbianceCompact" theme from gnome-look.org, which can be found [here](http://gnome-look.org/content/show.php/AmbianceCompact?content=124125).  Of course if you're having troubles with the above then the rest of this guide will probably be a nightmare for you!  Still I recommend doing *something* with your themes to make them more compact!

It really makes a difference!

**Remove unused panel applets...**

Here's another annoyance.  Shuttleworth in his brilliance surpassing mortal men has decided to break the system tra^^^notification area because it was [inconsistent](http://design.canonical.com/2010/04/notification-area/) by...wait for it--making it even [more](http://ubuntuforums.org/tags.php?tag=notification+area) [inconsistent](http://ubuntuforums.org/tags.php?tag=system+tray)!  

Just to make things more fun, if you try removing items the way it worked in previous versions of Ubuntu you can end up "losing" items completely unrelated to the one you removed!

Thankfully there is a way to remove stuff selectively if you follow the advice given by [Didius Falco](http://ubuntuforums.org/showpost.php?p=9165116&postcount=2)...

[quote=Didius Falco]If you want the "envelope" gone, remove the indicator-messages package, and keep indicator-sound (which is for the volume) and indicator-application installed.  Don't remove indicator-applet, which is the host applet that all of the above plug into.

```
sudo aptitude purge indicator-messages
```

You may have to log out to make things show up or go away the way you want them to.

NOTE: This does not fix the spacing issues or the random movement of icons which seems to happen once in a while.

**make panels customizable again!**

One of the better features in previous versions of Ubuntu was the ability to set your own panel backgrounds.  Then mysteriously the feature disappeared around the release of Jaunty or Karmic.  Thanks to stinkeye you can customize your panels again:

> **stinkeye said:**
> In your theme's gtkrc file search for panel
and look for a line that looks similar to
```
bg_pixmap[NORMAL] = "panel.png"
or
bg_pixmap[NORMAL] = "panel_bg.png"
```
Put a hash mark(#) in front of that line.

Your theme will be in ~/.themes or /usr/share/themes

If it's in /usr/share/themes you will need to edit as root.
```
gksu nautilus /usr/share/themes
```

Log out and Log in for changes to work.

Thank you very much stinkeye!  You have no idea how much I missed being able to do this!

Now that we've gotten the GUI worked out a bit, let's move on to other things.  We'll come back to making the mouse work as it did in previous versions of Ubuntu further on down...

**Updates!**

Apparently there are all kinds of issues in Lucid still being worked out and fixed.  Who knew?  Now is the time to try to connect to your WiFi or plug in your ethernet cable.  If using WiFi, you'll probably have to reconnect a few times by toggling the Fn + F2 key a few times if it doesn't connect right away.  Keep enabling and disabling until you get somewhere, it'll happen eventually.  (You're reading this somehow, aren't you?)

You'll notice there is a kernel updated listed in the update manager.  When you install it WiFi becomes even more flaky.  Oh joy!  maybe we should try installing something else?  I hear Red Hat Fedora works pretty good...LOL just kidding!

If you are doing this guide and reinstalling from a previous installation of Ubuntu Lucid Lynx you should have backed up your *.debs as recommended up above, otherwise you're going to be waiting quite a bit as Ubuntu downloads and installs updates...

Assuming that you have already copied the *.debs over to the proper directory or are prepared to download them all now, let's open Software Sources and add a repository which will fix our WiFi issues.

```
System-->Administration-->Software Sources
```
You will be asked for your password, enter it and the Software Sources applet will load, you want the tab that is named Updates.

You should see a screen like this one:

[[img]http://img833.imageshack.us/img833/214/screenshotsoftwaresourc.png[/img]](http://img833.imageshack.us/i/screenshotsoftwaresourc.png/)

See how the Unsupported updates (lucid-backports) list box is checked?  You need to check it also.  Now click close and reload the repositories as instructed.

Once you've reloaded the repositories open the terminal and type in the following:

```
sudo apt-get install linux-backports-modules-wireless-lucid-generic-pae
```
The above package is a metapackage pointing towards the latest version of the wireless modules for the PAE kernel.  Installing it will automatically add the linux-image-generic-pae package, another metapackage which will install the latest version of the kernel with PAE support.  You'll notice this kernel is intended for systems with more than 4GB RAM according to Synaptic, yet strangely enough this is the only default kernel that has good WiFi support for my eeepc and I only have the stock 1GB RAM installed.

Before rebooting the eeepc you should probably add the wireless card to the modules list, so you'll want to run the following commands:

```
sudo gedit /etc/modules
```
At the end of the file add this:

```
rt2860sta
```
Save and reboot.  Your wireless should be working again without issues.

It works.  That's all I know.  And much much easier than the older method endorsed by this guide, included below for completeness sake:

> **bornagainpenguin]**WiFi doesn't work?  Install the modules from Ralink!**

For whatever reason the drivers for the RT2860sta WiFi card found in many netbooks was broken in the last few kernels.  There are all sorts of reasons for this, but as far as I can see the chief one seems to be politics.  Whatever.  The fact is drivers *do* exist and the manufacturer has provided them, unfortunately you'll have to compile these yourself.

I am aware that an alternate kernel is [available](http://rsalveti.net/pub/ubuntu/kernel/lucid/) from Ricardo Salveti that works for some people.  I never had any success with it though and there were reports of [bad side effects](https://bugs.launchpad.net/linux/+bug/496093/comments/131).  Also suggested as a possible fix is to update to the latest [bleeding edge kernel](http://kernel.ubuntu.com/~kernel-ppa/mainline/) possible.  errr...yeah, I think I'll stick with the manufacturer's drivers even if I have to redo them every kernel release...

Fortunately there are guides for working around this long standing bug, including one from [Fass over at Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=1045703) who walks you through installing the module on Intrepid.  Sheesh!  This bug really has been around for awhile, hasn't it?  Thankfully there are more updated guides available we can follow...

Sven6210 (also from UbuntuForums) [updates the instructions](http://ubuntuforums.org/showthread.php?p=9281405) given by [Chris Barker](http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html) and fills in some of the information he glossed over.  Namely what to do when one of the files mentioned by Barker gets a character encoding error!  Thankfully Sven6210 walks us through it:

[quote=Sven6210]Here the description step by step:

**Step 1**
Download latest RT2860 driver source code from Ralink

Go to [http://www.ralinktech.com/](http://www.ralinktech.com/)
Click on Software
Click on Linux

Download the driver "RT2860PCI/mPCI/CB/PCIe(RT2760/RT2790/RT2860/RT2890)&#8220 said:**
> 
As do I.  I made some modifications from the original directions as listed, mostly by adding the exact kernel name as of this writing.  If you updated like you were supposed to then there shouldn't be any issues here.  You *did* update, didn't you?  Otherwise as it says in the instructions, you'll have to navigate to the directory and see which kernel you're running.
Again, please note that this is no longer the way I recommend to get WiFi working; it is only included for the sake of completeness.

[b]Make the mouse work right again!
*Restoring the previous handling of middle-clicking links in Firefox*[/b]

Randomly upon the release of Karmic 9.10 Canonical developers decided to [change the two finger middle click](https://bugs.launchpad.net/ubuntu/lucid/+source/gnome-settings-daemon/+bug/432814) that had been the default for well over two years and three releases of Ubuntu.  Worse they removed any way to revert the changes.  The only solution for many people on Karmic was to drop in a replacement module compiled by people on the Italian eeepc forums and hope an update didn't break things.  Thankfully there is an easier way on Lucid, using a PPA.

Just add Yuri Khan's PPA to your system in terminal:

```
sudo add-apt-repository ppa:yurivkhan/proposed
```
Now update for the system to find the fixed gnome-settings-daemon...

```
sudo apt-get update
sudo apt-get upgrade
```
Hit **y** to allow the update to download and install then reboot for the changes to take effect.

Back?  Now you need to change an entry in the gconf-editor.  Get the run box by hitting Alt+F2, then type in "gconf-editor" no quotes and navigate your way to:

```
/desktop/gnome/peripherals/touchpad
```
Then you will need to change the keys to your preferred handling:

> **Yuri Khan]Edit values tap_button_rt, tap_button_rb, tap_button_lt, tap_button_lb, tap_button_1, tap_button_2 and tap_button_3 as desired. These are, respectively: right top, right bottom, left top, left bottom, one-finger, two-finger and three-finger taps. (Corner tap settings are in Lucid version only. In Karmic, gnome-settings-daemon didn&#8217 said:**
> 
Thank you very much!  This has been a life saver on my eeepc!

While we're configuring the mouse, now might be a good time to enable two finger scrolling again too.

```
System-->Preferences-->Mouse
```
On the **Touchpad** tab there will be an option to allow this click it and your mouse will function again like it had under the last several versions of Ubuntu.

Depending on your personal preferences you can also go to the **General** tab and enable the *Locate Pointer* option which will show the mouse position when the control key is pressed.

**Laptop_Mode?**

**NOTICE:** There have been reports of problems with this next tweak.  I haven't had any issues with it on my eeepc 901L, but DavAlan reported having some trouble on his eeepc 900 after using this.  Your mileage may vary...

[quote=DavAlan]Just brought my raid lvm install down earlier when the updater installed HAL for some weird reason (warning - the added "nohal download" line did not work out so well :S )
The following may be removed in an update unless I hear confirmation that the errors caused by HAL being installed despite the **--no-install-recommends** flag being used were a one time thing.  I am including it for now for completeness sake.

[quote=bornagainpenguin]Thanks to the removal of HAL it is a bit tricker to get Laptop_Mode_Tools installed.  Also there will be a warning about removing the ""pm-utils-powersave-policy"  package"  which so far as I can tell can safely be ignored unless you were planning on writing your own power management scripts...

The command you want is:

```
sudo apt-get install --no-install-recommends laptop-mode-tools sdparm ethtool
```
The **--no-install-recommends** should prevent installation of HAL.  All credit (and blame) can be given to the [Doesn't Not Compute](http://mulenmar.wordpress.com/2010/03/25/ubuntu-netbook-edition-10-04-beta-1/) blog, where I saw this.[/quote]

**Power savings?  Kind of...**

**scripts**

Previously I had posted here a list of scripts by Axx83 from the Ubuntu Forums, but many of them were reported to be less than useful in Lucid and I didn't even enable them at all in the last few installs I did.  If you still want them or feel that they make more of a difference than I think feel free to post and explain why and what your results are.  For now these are no longer included directly into this increasingly large post.  You can still find the original posting [here](http://ubuntuforums.org/showthread.php?t=1326333).  Bear in mind they were originally written for Karmic and may behave wildly differently on Lucid.

**eee-control**

Since the posting of this guide in its previous form, marx (Grigori Goronzy) has surfaced again with a new release of his application:

[quote=marx]2010-05-23  Version 0.9.6
Hi, I'm still alive!
Version 0.9.6 contains various bugfixes plus support for newer DBus APIs and Linux kernels. The deb package is designed for Ubuntu Lucid. A few rough edges remain, but everything works fine for me.
What's new:
* Disabled hotkey-setup/hotkey handling - now handled correctly out of the box
* Use upstart instead of sysv init
* Switched to UDisks and UPower DBus APIs
* Cleaned up eee-control-setup
* Misc fixes
Ubuntu package: Lucid (10.04)
Get the source code from Git: git clone git://greg.geekmind.org/eee-control.git && cd eee-control && git checkout 0.9.6

PS: Version 0.9.5 was supposed to introduce compatibility for Ubuntu Karmic, but was never released.[/quote]

So now we know.  I've installed the application and it works perfectly for me, triggering the WiFi, setting the powersaving mode automatically when the eeepc is taken off the power supply.  If you're tied to Ubuntu this is an application you want installed!

**Other power management options...**

Since the last posting of this guide there have been updates to Fewt's Jupiter applet, which while no longer supported on Ubuntu is not explictedly hostile to it either.  Packages and information can be found [here](http://www.statux.org/content?page=catalog&catagory=1&product=jupiter).  In case you were thinking of switching to Fedora, the good news is that Fedora *is* offcially listed as a supported distro by fewt!  Just saying...

There is also a new one called entwjne written by eeeuser.com member Arvigeus.  Unfortunately it is a command line only application for the time being, but people wishing to help speed development along can help by beta testing.  See entwjne [here](http://forum.eeeuser.com/viewtopic.php?id=86139).

**BatteryStatus vs ye olde battstat**

One of the more grievous removals in Lucid was the battstat applet which was more accurate an indicator on eeepcs than the default gnome-powermanager battery applet.  In previous versions of Ubuntu this was only a few clicks away and could easily be added to your system tr^^^notification area.  In Lucid Canonical decided to simply make it impossible to launch the applet despite it still being listed as present.  If you were to open Synaptic and do a search for "battstat" (no quotes) you would discover it still listed in the information panel under the gnome-applets package.

Despite there being 192 people who went through the effort to create a Launchpad account, never mind the twelve duplicate threads on this issue [this guy](https://bugs.launchpad.net/indicator-application/+bug/527458/comments/12) has decided it is unnecessary.

[img]http://img148.imageshack.us/img148/8536/idioth.png[/img]

Thanks alot Mark.  You're a brick, a real... $#&* brick, pal!

Thankfully there are still options available:

[QUOTE=perky]**To install:**  Save and extract BattStatus.zip to a temporary directory, then cd to where you extracted the files and type:

```
sudo sh install.sh
```

GNOME Panel will reload and the applet should now appear in the '**Add to Panel**' list as '**Battery Status Applet**'.

**Known bugs:**

Most bugs are caused by conflicting gconf settings from older versions and can be fixed by:
[LIST=1]
[*]Removing the applet
[*]Running as regular user: gconftool-2 --recursive-unset '/apps/battery-status-applet'
[*]Re-adding the applet
[/LIST]

The error: ...OAFIID:GNOME_PythonPanelApplet... means that the OAFIID in the .server file does not match the last line in the .py file.
Installing the latest version fixes this.

Other distros display a default icon unless Humanity icon theme is installed (will be fixed when I get around to making my own icons)

Thanks to all that have helped identify bugs 

**Uninstall instructions:**
```
sudo rm /usr/lib/bonobo/servers/battery_status.server
sudo rm /usr/local/bin/batteryStatus.py
```[/QUOTE]

If you do not have an account at the UbuntuForums you will not be able to download the applet.  Here's a mirror:

```
http://www.mediafire.com/?fsq4ustr8iosvfc
```

Otherwise if you really prefer to use the old battstat that was included with every previous version of Ubuntu you can try this dirty hack:

[quote=bornagainpenguin]I was able to "cheat" by going to the nearest Debian mirror and installing the appropriate gnome-applets AND gnome-applets-data for my version of Gnome.  I ignored warnings that I was installing newer versions of the software than what was in the channel and after some dependencies were installed and I did a quick logout I was able to add back the battstat icon to my panel.

Here's a heads up for any Canonical developers: If you want to remove or "depreciate" a piece of system software, it's usually a good idea to make sure that the replacement works just as well as what is being removed...[/quote]


What I did was go to:

```
http://debian.osuosl.org/debian/pool/main/g/gnome-applets/
```

Then download these two files:

```
gnome-applets_2.30.0-3_i386.deb
gnome-applets-data_2.30.0-3_all.deb
```

Ubuntu Lucid demands that you have a later version of gconf2 and libnotify1 installed, so you'll have to grab those too.

Go to:

```
http://debian.osuosl.org/debian/pool/main/libn/libnotify/]
```

download this file:

```
libnotify1_0.5.0-2_i386.deb
```

Go to:

```
http://debian.osuosl.org/debian/pool/main/g/gconf/
```

download this file:

```
gconf2_2.28.1-3_i386.deb
```

Now from within the terminal navigate to the directory where you downloaded these files and enter this command:

```
sudo dpkg -i *deb
```

Do a restart and the battstat applet will be available again  right where it used to be before developer stupidity caused Canonical to remove it from the distro.  Just add it to the panel and disable the gnome powermanager battery icon in preferences.

[IMG]http://img405.imageshack.us/img405/4051/battstat.png[/IMG]

Personally I prefer the older battstat applet, but am happy to see Perky's battery status applet being devloped and I have high hopes for it still being around even after Canonical manages to completely cripple battstat from working even with this typs of dirty hack.

NOTICE: Canoncial could invalidate this dirty hack at any time so if you are nervous you are best to just use Perky's applet.

**Curb the heat by using the latest video drivers**

Personally I'm still not convinced it is any one thing that causes the eeepc to no longer overheat, but a combination of little things that each reduce the heat bit by bit.  Nevertheless I've been using this PPA also and have definitely seen improvements in both heat reduction and video playing.

[quote=Vredley]Oh, and one other thing - my 4G seems to be running a bit cooler since I installed the latest stable video driver from the X-swat PPA:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)[/quote]

To do this you need to add the repository:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

Then you'll need to refresh and upgrade your packages:

```
sudo apt-get update
sudo apt-get upgrade
```

If for some reason the xserver-xorg-video-intel package gets held back, you can install it manually:

```
sudo apt-get install xserver-xorg-video-intel
```

This will pull in the missing packages holding you back and allow everything to install.  To see things take effect, reboot the eeepc.

**Elevators**

A few tips for improving battery via passing along options to the kernel in Grub2.  **Fair warning:** the acpi_osi option may not apply to all eeepcs, although they have been very helpful to many users with eeepc 1xxx models!  Your mileage may vary.

> *Any text editor will work at reading the below files.  nano, kate, gedit, etc.  You will have to be root or use sudo before the commands.*

e.g.
*$ sudo gedit /etc/default/grub*

**_Grub_**
1. Change IO scheduler:
```
elevator=deadline
```
2. Use the integrated HPET timer (saves about 30 CPU wake ups per second)
```
hpet=force
```
3. Make sure the eeepc-laptop kernel module is loaded properly (does not load correctly with kernel 2.6.32):
```
acpi_osi=Linux
```
$ lsmod | grep eee   #  if nothing is listed, it isn't loaded

How to load the above in grub2:
/etc/default/grub

```
GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux elevator=deadline hpet=force quiet"
```
# update-grub2
I've also seen reports that elevator=noop is a good option to use instead of elevator=deadline.

I recommend changing the grub2 configuration to wait a few seconds while testing these tweaks to allow you to edit them out if they prevent booting.  to do that simply make the following changes:

Where it says **GRUB_HIDDEN_TIMEOUT=0** add a "#" in front of it to allow the count down to work again.

```
# GRUB_HIDDEN_TIMEOUT=0
```
Then change the count down from ten seconds to something smaller, like three or two if you're fast enough to hit the keys before it starts.  You can do that by changing the number here:

```
GRUB_TIMEOUT=10
```
```
GRUB_TIMEOUT=2
```
Save the file and as instructed above don't forget to update the configuration!

```
 sudo update-grub
```
Reboot to see the changes.

**Still to do and errata...**

I'd like to add a small section on what can be removed for space saving reasons and lack of usefulness to the average user.  Things to include here are fspot, brasero, tomboy etc.  Usually I just use the guide [here](http://ubuntuforums.org/showthread.php?t=820804), but it is sadly out of date and much *much* care needs to be taken with this or users will find themselves without a network manager installed!

More tweaks and something on the benefits of using Nautilus Elementary:

[IMG]http://img823.imageshack.us/img823/6494/2iw13yc.png[/IMG]

**Next version...**

I want to investigate adding [Konstantinos Natsakis'](https://launchpad.net/~cyfex/+archive/ppa) repository as a possible solution to the theming issues mentioned above.  Depends on whethe ror not it actually solves the problem.

I'd still like to explain how I set up my /data with symbolic links and hopefully have a better way to do it than I currently use.  I had a [thread](http://ubuntuforums.org/showthread.php?p=9282535) open on UbuntuForums on the subject, and the guy responding was great about trying to help me figure things out, but unfortunately much of what was posted went waaaaay over my head.  Maybe someone from the eeeuser.com forums can take it and run with it?

Would like to know if there is a good way to back up and restore a music collection and podcast directory like can be done in iTunes, but using Banshee or Rhythmbox?  If there is it should definitely be added to the guide for those of us who distro hop!

Feel free to suggest items to add for future versions!

Hopefully this will be of use to someone.  Considering it has taken me nearly an entire day to do, I certainly plan on using it myself in the future...  Nice to have all the information in one place, you know?

--bornagainpenguin

EDIT -- added tip to customize panel backgrounds

---

### Post by bornagainpenguin on 2010-04-30
**RESERVED for future posting**

---

### Post by Macchi on 2010-05-01
> PS: Anyone know how to get eee-control to do cpu scaling? I installed this package, but my eeepc is still running hot..

I am also interested in a solution. Our EEEPC 701 with Lucid is running very hot, no fan nor CPU scaling! I fear the risk for hardware damage if overheated.  

Actually we have two similar EEEs in the family, a 701 and a 900. (Its one laptop per child!) 
Sad to say, but both netbooks are having similar problems with Ubuntu 10.04 Lucid, namely:

* The fan is not activated and the EEE 701 runs HOT. 
* No processor scaling, thus battery time is shorter than it could be.
* Wrong indication of the last full capacity of the battery (EEE battery uses percentage and not mA )
* No animated splash on boot (solution in earlier posts of this thread)
* Microphone works barely and is very noisy
* Evolution and Rhythmbox do not work well with a limited screen of 800x480 of the EEE 701  
* Default theme has to be adjusted (solution in earlier posts of this thread)
* Trackpads are dead after returning from suspend
* Multi-touch trackpad of the EEE 900 does not work. 
* The package usb-modeswitch has to be installed manually if using a wide range of mobile broadband modems (this is a generic problem for all Ubuntu 10.04 systems)

Regarding the EEEs, the 9.04 release was easier to live with than the original Xandros. Unfortunately the number of new and old bugs on the 10.04 LTS is alarming. The problem is that the convergence of Ubuntu is very slow, and when everything ever becomes "perfect"  then the machines will certainly be more than obsolete! Actually these EEEs were already obsolete a year ago! 


PS: As a reference I would like to mention that I have been using GNU/Linux since 2002 and Ubuntu since Hoary 5.04. Now I have started to feel very concerned about the practical future of GNU/Linux for business applications. I am not into systems development anymore and I would describe myself as a conceptual systems integrator, looking for integrated open software solutions for small and medium organizations. I usually test a dozen of netbooks, laptops, workstations and servers with different distros and releases.

---

### Post by theSuperman on 2010-05-02
Ive mostly been seeing performance issues while clicking and dragging files around. Nautilus runs at 100% cpu usage for a few seconds. No errors in logfiles. 

Also, compiz doesn't work right with an external monitor.

Running this: 
'xrandr --output LVDS1 --off --output VGA1 --auto'
allows me to turn off my internal screen, leaving only my external one on. But if I then run totem, it switches on my internal screen, makes that primary, and then sets up my external screen as an extended desktop. 

Running 'xrandr' with no other options does the same. 
So those are the issues I am seeing.

---

### Post by danb1974 on 2010-05-02
Fix the backlight on 1005p (probably other similar models too): edit /etc/default/grub, add acpi_osi=Linux acpi_backlight=vendor to GRUB_CMDLINE_LINUX_DEFAULT and run update-grub

Also you can try to add fastboot to boot parameters (too lazy to check if it is still not default, in older kernels it improved the boot time by a few secs by parralel initializing of some subsystems like ata, usb)

If you have a ssd, add elevator=deadline (later edit: typo fixed, thanks [bornagainpenguin]("http://ubuntuforums.org/member.php?u=6601"))

---

### Post by bornagainpenguin on 2010-05-02
> **danb1974 said:**
> If you have a ssd, add elevator=dealine

I think you meant elevator=*dea**d**line*, right?

--bornagainpenguin

PS: Those other tips are new to me and I'll have to see if they do anything good for me on my eeepc 901L when I get a chance to try Lucid on my eeepc again later.  Right now I have to get ready for Church, will try to add those tips to the first post once I've had a chance to test them out and organize the information.  Thanks for contributing!

---

### Post by bornagainpenguin on 2010-05-03
Just saw this mentioned in the comments on [DistroWatch.com](http://distrowatch.com/weekly.php?issue=20100503)...

[quote=Jesse]**Lovely. So what you are saying is that it looks like *buntu regularly calls home, just like the rest of the corporate shovelware OSes. How "helpful".**

*No, I'm not saying that. What I said was the service is doing something in the background. It could be checking for folders to sync, it could be monitoring file system changes, it could be aggressively polling for status changes. Or, maybe it is contacting the One servers. What I was saying is it was doing something when I felt it should be idle. I'm not certain the One service was accessing the network, but it was churning on the CPU.*[/quote]

Could someone with Lucid on their eeepc try disabling\removing UbuntuOne and report back if this makes any difference with CPU scaling or with how hot the handrest gets?  I seem to recall similar issues with Tracker when it was first introduced in Gutsy or around-there-abouts and people reported the service was constantly polling and causing issues.  Could this be a similar issue with UbuntuOne?  The fix then was in removing the application and services, it could be again for this...

--bornagainpenguin

---

### Post by bornagainpenguin on 2010-05-04
Bump for update

---

### Post by nereid on 2010-05-10
I tried installing the RAlink driver, and at first, it worked. Now since about two days ago, wireless is back to failing to authentication failure.

I even tried to install the 2.6.33 kernel, but that was a real disaster, as the touchpad didn't work anymore and the grafics were also borked.

Has anybody got a working hibernate? If my eeePC goes into hibernate, it refuses to switch off.

This whole mess is really a big regression in comparission with Karmi and at the moment I'm really pondering on downgrading again. Come on, Lucid should be a LTS version...This isn't up to the usual quality of LTS versions.

---

### Post by bornagainpenguin on 2010-05-11
MAJOR UPDATE POSTED.

/me off to eat now.  Food good...brain tired...

--bornagainpenguin

---

### Post by bornagainpenguin on 2010-05-13
**BREAKTHROUGH:**  As some of us have begun to suspect, many of the bugs we're encountering are kernel related, this next tip seems to confirm those suspicions...

I just installed the latest kernel (as of this writing) from Daniel Hollocher's [linux-ck ppa](https://launchpad.net/~chogydan/+archive/ppa), and by doing so dropped my wakeups-from-idle per second to Hardy Heron levels!  Most welcome of all, using this kernel seems to stop the jbd2 process from doing so many writes to the disk on ext4!  I tested this out on my desktop and have yet to confirm on my eeepc (reinstalling as I write this message) but this looks to be a major breakthrough in getting performance to work again and getting idling to function on battery in a more sane way!

[quote=Daniel Hollocher]Test ppa for packaging the ck patchset. See lp:#424927

To add this ppa: 
```
sudo add-apt-repository ppa:chogydan/ppa && sudo apt-get update
```
To install:
```
sudo apt-get install linux-ck-generic linux-ck-headers-generic
```
To get help, please visit: [http://ubuntuforums.org/showthread.php?p=9249519](http://ubuntuforums.org/showthread.php?p=9249519)[/quote]
Make sure you edit grub to set the timer so you can be sure of selecting the right kernel at boot.  Also bear in mind the need to redo the WiFi if you're using the Ralink drivers in the guide!

That's the good news.  The bad news is I seem to be having issues getting the fan to run properly.  Installing the kernel above brings all kinds of benefits in latency and in reducing wakes from idle, but it also makes the system behave strangely with regards to the i810 driver.  Also. sensors doesn't seem to be automatically loading the coretemp modules unless you run the detection sequence and add it to modules.  The fancontrol script doesn't seem to be doing much and the eeepc (like many many other mobile devices this release) runs hot burning my hands on the hand rest and  making me fear for the life of the device if I keep trying to get Lucid to run on it.

Unless someone has good news for me I'm about to abandon ship for either Debian or rolling back to Hardy again...

--bornagainpenguin

--bornagainpenguin

---

### Post by bornagainpenguin on 2010-05-24
[eee-control]("http://greg.geekmind.org/eee-control/") has been updated for Lucid!  I figured people following this thread might be interested in hearing this bit of good news...all three of them!  ;)

--bornagainpenguin

---

### Post by milkyspit on 2010-05-24
> **bornagainpenguin said:**
> [eee-control]("http://greg.geekmind.org/eee-control/") has been updated for Lucid!  I figured people following this thread might be interested in hearing this bit of good news...all three of them!  ;)

--bornagainpenguin

That is darned good news! :)

I've got Lucid running on an original Eee PC 4G that my wife uses for home and graduate school work. My problem is the wireless is completely non-functional under Lucid. Any tips on what to do to get that going? The rest of the system is working nicely, so getting the wireless running would make it just about perfect for her needs.

---

### Post by bornagainpenguin on 2010-05-24
> **milkyspit said:**
> That is darned good news! :)

I've got Lucid running on an original Eee PC 4G that my wife uses for home and graduate school work. My problem is the wireless is completely non-functional under Lucid. Any tips on what to do to get that going? The rest of the system is working nicely, so getting the wireless running would make it just about perfect for her needs.

That's the 701 model, right?  That's strange as from what I've seen most of those models usually work out of the box in most forum posts.  Do you know which model WiFi card you have?  A good bet would be to try the eeeuser.com forums to see if someone more familiar with your specific model eeepc is able to walk you through what worked for them.  Good luck!

--bornagainpenguin

---

### Post by katzman2 on 2010-05-24
Will this problem have an effect on desktop units.  My desktop keeps querying the battery and then logging me out.  The only clue is that the message "checking battery state" comes onto a black screen (like the old dos screen) and that is all I can read but the next screen to come up is the login window.
Thanks
katzman2

---

### Post by bornagainpenguin on 2010-05-25
> **katzman2 said:**
> Will this problem have an effect on desktop units.  My desktop keeps querying the battery and then logging me out.  The only clue is that the message "checking battery state" comes onto a black screen (like the old dos screen) and that is all I can read but the next screen to come up is the login window.
Thanks
katzman2

???

I'm sorry I'm not sure I understand the question.  Do you have an eeepc?

--bornagainpenguin

---

### Post by bornagainpenguin on 2010-05-26
SIGH

I'm already rolling back to Hardy again as I contemplate a Fedora attempt.  I had Lucid installed with reiserfs and it just crashed on me hard leaving me with a very corrupted file system.  I'm not sure what exactly the cause of the problem is (I suspect the fact it was running at near 145 F might have had something to do with it myself) regardless I am done with this pile of steaming $#*! called Lucid Lynx.

If anyone else wants to try taking over the thread they're welcome to it.

--bornagainpenguin

---

### Post by milkyspit on 2010-05-26
> **bornagainpenguin said:**
> SIGH

I'm already rolling back to Hardy again as I contemplate a Fedora attempt.  I had Lucid installed with reiserfs and it just crashed on me hard leaving me with a very corrupted file system.  I'm not sure what exactly the cause of the problem is (I suspect the fact it was running at near 145 F might have had something to do with it myself) regardless I am done with this pile of steaming $#*! called Lucid Lynx.

If anyone else wants to try taking over the thread they're welcome to it.

--bornagainpenguin


I'm sorry to hear that and realize you must be incredibly frustrated. I don't think Lucid is a pile of steaming $#*!. It's been working well for me on three different systems, one of which is my Eee PC 4G (=701).

You've helped several of us a great deal with this thread, and from me at least, thank you! Incidentally, my wireless issue has been resolved, and I'm ashamed to admit that I had wireless disabled in BIOS... once enabled in BIOS, it worked fine. In a weird way your assertion that wireless just tends always to work with Ubuntu on these Eee PC units was what led me to dig deeper to find my (very embarrassing) problem.

Gotta ask: why ReiserFS? It's basically unsupported at this point, the lead developer is in prison, the company has essentially folded its operations... more the the point, its performance tends not to be any better than ext3 and certainly is inferior to ext4, and ReiserFS has some nasty vulnerabilities which can lead to, well, pretty catastrophic filesystem messes. Was there a particular reason you were running it as opposed to one of the alternatives? I'm just curious, sorry for prying.

---

### Post by bornagainpenguin on 2010-05-26
> **milkyspit said:**
> I'm sorry to hear that and realize you must be incredibly frustrated. I don't think Lucid is a pile of steaming $#*!. It's been working well for me on three different systems, one of which is my Eee PC 4G (=701).

I have had Lucid on three different systems, one of which is my eeepc 901L.  For the most part on the desktop Lucid seems to work pretty well, only falling down in cosmetic issues like the annoying notification area bug that Canonical and Gnome developers seem to be intent on ignoring.  Canonical as they chase after "windicators" and Gnome as they gear up for 3.0.  Other issues seem to have to do with the kernel and as such really are across all distros at this point unless they patch their kernels intensively...

> **milkyspit said:**
> You've helped several of us a great deal with this thread, and from me at least, thank you! Incidentally, my wireless issue has been resolved, and I'm ashamed to admit that I had wireless disabled in BIOS... once enabled in BIOS, it worked fine. In a weird way your assertion that wireless just tends always to work with Ubuntu on these Eee PC units was what led me to dig deeper to find my (very embarrassing) problem.

Errm...no.  That's not what I said exactly.  When I said WiFi seems to mostly just work--that was specific only to those earlier celeron 7xx models of the eeepc.  They use a different wireless card than the other models do and that card seems to be better supported over all.  I'm glad the issue was resolved for you, but I had to clarify that WiFi does not just work on ***all*** eeepcs...that would not be true at all!  It just seems the 7xx models and celeron based models work better with their hardware being detected and working.

> **milkyspit said:**
> Gotta ask: why ReiserFS? It's basically unsupported at this point, the lead developer is in prison, the company has essentially folded its operations... more the the point, its performance tends not to be any better than ext3 and certainly is inferior to ext4, and ReiserFS has some nasty vulnerabilities which can lead to, well, pretty catastrophic filesystem messes. Was there a particular reason you were running it as opposed to one of the alternatives? I'm just curious, sorry for prying.

Don't apologize.  It was an experiment to see if the file system work be faster at boot like ext4 is except without the runaway process described in the first post.  ext3 seems to work just fine, but it is a bit slower and I really like to be able to show off the boot of my eeepc as a method of boosting Linux.  The boot and the crisp fonts are two of the biggest features I always show off Linux with because the legibility and boot times of most Windows based netbooks is a joke.  Compiz always gets a good response also, especially when they see using it integrates with the work flow and doesn't slow the system down like using similar features on Windows does.

The fact I get all this and am barely touching the one gigabyte of RAM the system comes with is always an eye opener!

The sad truth is there aren't very many options in the installer to allow a user to choose from.  Of the options available I've gotten good results with only ext2-ext4 and reiserfs.  The other file sysetms have fallen down on me when I've tried to use them or insist on doing horrible disk checks every third boot.  Then there is the bonus of reiserfs being supported by Acronis True Image, which allows me to pull out a mostly updated and patched system to test things quickly otherwise it would take me nearly a day to do all the stuff needed to install Hardy again once I failed to get an upgrade to work...

Ordinarily I'd have not bothered with reiserfs for all the reasons you listed but it was recommended in the thread I had on the Ubuntu section of the eeeuser.com forums as a replacement for ext4 when it became clear it was behind some of the constant disk activity when the system was supposedly at "idle" but....  SIGH.

I'm glad you found the posts to be useful!

--bornagainpenguin

---

### Post by milkyspit on 2010-05-26
> **bornagainpenguin said:**
> ...Then there is the bonus of reiserfs being supported by Acronis True Image, which allows me to pull out a mostly updated and patched system to test things quickly otherwise it would take me nearly a day to do all the stuff needed to install Hardy again once I failed to get an upgrade to work...


On my primary two laptops I've been running LVM2 and using its snapshotting capability along with fsarchiver and an external hard drive to make compressed filesystem images. The beauty of this approach is that I can do so with a live system, without introducing corruption. On the flip side, it's quick and painless to restore the saved image, and I can even restore to a different filesystem than had been in place at the time of image creation. I've come to love this approach as it has, for the first time, given me the ability to keep robust sets of backup images without suffering significant downtime. You might look into that to open some more options beyond TrueImage, if that helps anything.

---

### Post by bornagainpenguin on 2010-05-26
> **milkyspit said:**
> On my primary two laptops I've been running LVM2 and using its snapshotting capability along with fsarchiver and an external hard drive to make compressed filesystem images. The beauty of this approach is that I can do so with a live system, without introducing corruption. On the flip side, it's quick and painless to restore the saved image, and I can even restore to a different filesystem than had been in place at the time of image creation. I've come to love this approach as it has, for the first time, given me the ability to keep robust sets of backup images without suffering significant downtime. You might look into that to open some more options beyond TrueImage, if that helps anything.

That sounds interesting.

I tried clonezilla when my eeepc was nbew (almost two years ago now) and it didn't seem to like my SSDs at all.

Do you have a link to a tutorial written for newbies explaining your method?  Also does using your method restore files like the fstab?  I used to use remastersys a bit back until I realized it wasn't restoring the original fstab and I had to readd those and other settings again manually every time I restored which was a PITA.  Plus I could never be sure what settings were restored and which ones weren't meaning I had to recheck them all--easier to just do a reinstall if I have to do that!

In Acronis after a restore everything is back the way I had it and I don't have to do anything except update, rescan my music collection in Banshee and redownload any podcasts.  It helps that I store my music on an SD card formated as an ext3 allowing me to use symbolic links to its folder in my /home.  Oh and the five minute restore times in Acronis aren't to be sneezed at.  Not that I'm too happy with the longer time it takes to make the image, but you take what you can get and the benefits so far outweigh the costs.

--bornagainpenguin

---

### Post by gbm31 on 2010-05-28
Here's another happy 10.04 user (netbook edition) with a 901.

I use ext2, so I didn't have to mess around with fstab.

I didn't set up a swap partition either, 2 gigs of ram will do everything...

Thank you for your thread!

I've found two new things to tune here: the grub options and the scaled themes. I'm already testing...

I can confirm that the newest eee-control (0.9.6.2) functions properly. The deamon loads properly. A minor bug still persists: bluetooth enabling.
What I've changed: I disabled the brightness override in the conf.


What bugs me: notify-osd stopped working for brightness-changes. the bug report was closed with a stupid comment, saying that some laptop models don't send notification events for brightness changes.
If this was the correct answer, why did it work before?

---

### Post by jwstolk on 2010-05-29
First, I would like to thank bornagainpenguin for all work he has done so far!

I have an eeepc 900, and still run the original Xandros, half broked, but with some tweaks and scripts, mostly to under-clock the CPU, even when plugged in, and set the screen both darker and brighter than the range offered by the bios.
It takes forever to boot, because it first boots the "simplified" interface and then re-boots the "advanced" interface. Another problem is that updates stopped installing, and most of the packages are so outdated that it's a nightmare to compile things from source.
Since I'm a happy Ubuntu user I found this page looking for eeebuntu vs. Ubuntu 10.4. (so far it looks like eeebuntu would isn't perfect either.)

I'll cross my fingers and hope that having a Celeron will avoid the CPU fan problems...
If I find anything interesting I will mention it here.

---

### Post by gbm31 on 2010-06-03
Little update:

notify-OSD works again for brightness changes after re-installing indicator-messages. (needed that for my pim)

---

### Post by kmkwood on 2010-07-05
Very, very sorry.  Wireless fix didn't work for me.

I am disappointed, too, that my 901 no longer recognizes the Asus rescue thumbdrive as bootable -- I can't even go back.

---

### Post by bornagainpenguin on 2010-07-21
> **kmkwood said:**
> Very, very sorry.  Wireless fix didn't work for me.

I am disappointed, too, that my 901 no longer recognizes the Asus rescue thumbdrive as bootable -- I can't even go back.

If you've not already formatted over Lucid, try plugging the eeepc into a ethernet connection and firing up synaptic.  From the repositories menu enable backports, then refresh the lists.  Now search for backports and find the linux kernel with PAE and the wireless modules from backports that go with the PAE kernel--this will make it work.

--bornagainpenguin

---

### Post by bornagainpenguin on 2010-07-31
New guide posted.

Is it too early to head to bed now?

--bornagainpenguin

---

### Post by markbabc on 2010-08-09
ok so instead of starting a new thread i thought i would post it here so i could be added to the OP if it gets solved. ever since i switched to ubuntu on my eeepc 900 from windows xp (i think it was ubuntu 9.04) the webcam and mic havent been working. this wasnt much of a big deal because i didnt use it at all but i recently got into using skype on my phone to talk to people and i would love to be able to use it on my netbook but i cant because the webcam does not work. i check my BIOS and it says the camera is enabled and i installed eee control and it says my camera is on but it is still not working. so anyone else have this problem that knows how to fix it?

---

### Post by clight9 on 2010-09-19
Hi, thanks for all this.  I'm a brand-new linux newbie; I gave up on Windows a couple years ago (been using a Mac since then), and so when I decided to get a netbook (EeePC 901), I put Ubuntu Netbook Remix on it right away.  However, it's taking a lot of getting used to.  Guides like this really help!

I had a question about the wireless fix you recommend.  At the moment, I have linux-backports-modules-wireless-lucid-generic installed; it allows me to connect to WPA/WPA2 protected networks, but fails to connect to a lot of other networks, at least from the experimenting I've done so far.  By cafe-surfing, I've tried a couple wireless networks that require no password; the network manager recognizes them and makes a serious effort to connect, but then eventually fails.  At least one other such network connected fine, though.

So: will it solve this problem if I uninstall the linux-backports-modules-wireless-lucid-generic package and install linux-backports-modules-wireless-lucid-generic-pae instead?  Also, will installing that package have any 'side effects' on my system?

EDIT:  I decided to give it a shot, and it looks like it did the trick, at least judging from my current wireless connection (which wasn't working with linux-backports-modules-lucid-generic).  Thanks so much for posting these tips!!

---

### Post by dgray_from_dc on 2011-02-01
Hello all,

I recently bought a eeePC 701SD on ebay, upgraded to 2GB of RAM and tried Maverick NBR.  I didn't like it.  Figuring it was better suited for an older netbook, I backed up to Lucid NBR and have been pretty happy with it.  It does everything I intended it to, and a few things I didn't expect like playing video from a uPnP server over WiFi with XBMC!!  Outside of the screen size being inconvenient at times, it performs well.  The only real complaint I have is that most of the time, when using Fn+F2 to turn WiFi on/off it hangs the system.  I have to do a hard reset which triggers a file system check (not too bad on an 8GB SDD, but it's the principle).  I will add that I haven't made any of the improvements in this thread as I just ran across it (the thread) today and haven't had a need to tweak anything since I've installed.

Would any of the changes here fix my problem?  If not, any suggestions?

---

### Post by bornagainpenguin on 2011-03-09
> **dgray_from_dc said:**
> The only real complaint I have is that most of the time, when using Fn+F2 to turn WiFi on/off it hangs the system.

I can't promise you anything considering that the eeepc 7xx and the eeepc 9xx run on two different boards and processors, but in general most of these should work regardless (excepting the ralink WiFi perhaps) and are general purpose tweaks that would help out on most netbooks.

Your specific issue with the Fn+F2 sounds like an older issue that was seen back in the Karmic or Jaunty days cropping back up again, so I encourage you to make a bug report about it on launchpad.

How to solve it?  Well the solution at that time was to install the latest version of eee-control that supported the hardware, perhaps this will help you now also?  You can find eee-control [here]("http://greg.geekmind.org/eee-control/").

Let us know how you make out!

--bornagainpenguin

---

### Post by arronbond on 2011-10-18
This EEE Pad is looking fantastic. I am glad knowing about this. Well I am using EEEPC. But looking for EEEPC skin covers, So that I can avoid it from the dust particles.


------------------------
[EEEPC skin covers](http://www.decalskin.com/)

---


---
title: "HOWTO: New Zens 4/8/16/32GB + Amarok + 7.10"
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by narehart on 2008-01-09
This is a how to on getting the newest Creative Zens 4/8/16/32GB models working under Ubuntu Gutsy Gibbon 7.10 with Amarok.

**THIS IS FOR 32 BIT USERS ONLY.  IF YOU'VE SUCCESSFULLY INSTALLED THIS ON A FRESH INSTALL OF A 64 BIT VERSION PLEASE CONTACT ME AND LET ME KNOW  WHAT STEPS YOU TOOK AND I WILL ADD A SECTION TO THE GUIDE.**

Open a terminal and let's start by removing the old libmtp:

```
sudo apt-get remove libmtp6 libmtp-dev libmtp-doc
```

Go ahead and get rid of Amarok too:

```
sudo apt-get remove amarok amarok-xine amarok-gstreamer
```

Make a directory to store some files we'll be working with:

```
mkdir /home/**YOURNAME**/libmtp
```

Enter the directory:

```
cd /home/**YOURNAME**/libmtp
```

Download the latest libmtp from [sourceforge]("http://sourceforge.net/project/downloading.php?groupname=libmtp&filename=libmtp-0.2.4.tar.gz&use_mirror=internap") and save it to the libmtp directory.

Extract the file:

```
tar xzvf libmtp-0.2.4.tar.gz
```

Enter the new directory that was created when you extracted the file:

```
cd libmtp-0.2.4
```

Let's download some dependencies for libmtp:

```
sudo apt-get install build-essential gcc libid3tag0-dev libgtk2.0-dev libnjb-dev
```

**Click on the following links and install the .deb packages:**

[libc6]("http://http.us.debian.org/debian/pool/main/g/glibc/libc6_2.7-5_i386.deb") [libmtp7]("http://http.us.debian.org/debian/pool/main/libm/libmtp/libmtp7_0.2.4-5_i386.deb") [libc6-dev]("http://http.us.debian.org/debian/pool/main/g/glibc/libc6-dev_2.7-5_i386.deb") [libusb-0.1-4]("http://http.us.debian.org/debian/pool/main/libu/libusb/libusb-0.1-4_0.1.12-8_i386.deb") [libusb-dev]("http://http.us.debian.org/debian/pool/main/libu/libusb/libusb-dev_0.1.12-8_i386.deb") [libmtp-dev]("http://http.us.debian.org/debian/pool/main/libm/libmtp/libmtp-dev_0.2.4-5_i386.deb")

Configure libmtp:

```
./configure --prefix="/usr"
```

Execute the make file:

```
make
```

Install libmtp:

```
sudo make install
```

Now we'll install Amarok from source. First, install the necessary development files 

NOTE: I've included some extra features here such as the ability to rip and burn cd's right from Amarok and iPod support. These are not necessary to get your Creative Zen working in Amarok but I feel they add to it's functionality:

```
sudo apt-get install kdelibs4-dev subversion unsermake automake1.9 kdebase-dev build-essential ruby ruby1.8-dev libtag1c2a libtag1-dev k3b libtunepimp5 libtunepimp5-mp3 libtunepimp-dev kdemultimedia kdemultimedia-dev libsdl1.2debian libsdl1.2-dev libvisual-0.4-0 libvisual-0.4-dev libvisual-0.4-plugins libgstreamer-plugins-base0.10-dev libxine-dev libfaad2-dev libgpod2 libgpod-dev
```

Download Amarok [here]("ftp://carroll.aset.psu.edu/pub/kde/stable/amarok/1.4.8/src/amarok-1.4.8.tar.bz2") and save it to the libmtp directory.

Go back into the libmtp directory:

```
cd /home/**YOURNAME**/libmtp
```

Extract Amarok:

```
tar xjf amarok-1.4.8.tar.bz2
```

Enter the new directory that was created when you extracted the file:

```
cd amarok-1.4.8
```

Configure Amarok:

```
./configure --prefix=`kde-config --prefix` --with-libmtp --with-libgpod
```

Execute the make file:

```
sudo make
```

Install Amarok:

```
sudo make install
```

Install the latest mtp-tools from [here]("http://http.us.debian.org/debian/pool/main/libm/libmtp/mtp-tools_0.2.4-5_i386.deb").

Now open Amarok. 

Go to Settings > Configure Amarok > Media Devices

Click on Add Device.

Choose MTP Device from the drop down menu then give your Creative Zen a name. Close the menu.

Power on the Creative Zen and make sure it's connected. Click on the devices tab and then click connect.

Voilà! The power of linux once again defeats proprietary consumer electronics!

---

### Post by entropic_existence on 2008-01-09
I had previously installed libmtp and amarok from the newest source code as you described above (minus the ipod support and cd ripping support in amarok). Amarok recognizes my player. However I went to install mtp-tools from the link you have posted but it can't satisfy the libc6 dependency, which is odd considering that libc6 is installed on my system.

---

### Post by narehart on 2008-01-09
You have to install the newest lib6.  In my post there is a series of downloads that includes the newest lib6.

Also, did you install the newest libmtp-dev? Amarok needs the dev files as well the regular ones to add any additional functionality (e.g. libmtp, libvisual, libtunepimp, libgpod).

---

### Post by liveforfunnow on 2008-01-10
i can't get mtp-tools .2.4-5 to install. in GDebi, i see:

> Error: Dependency is not satisfiable: libmtp7

libmtp7 is installed via the .deb, and reinstalled. any ideas?

EDIT: I get the same error when trying to install libmtp-dev_0.2.4-5

---

### Post by entropic_existence on 2008-01-11
Getting that same error. Incidentally installing the newer versions of libc6 et al., inisitally really screwed up my dependencies. Think I have recovered and fixed that though but lib-dev doesn't want to recognize that linmtp7 is installed. (old libmtp is not installed)

---

### Post by narehart on 2008-01-11
Sorry, guys.  The link was to the old libmtp7.  I fixed it.

---

### Post by nmsmith on 2008-01-12
Thanks for this: I'm following the instructions as I write . . . 

I have one question and one concern though.

You mention installing a bunch of libraries to enable ipod support and cd burning, but doesn't amarok have these in its native ubuntu .deb form?

Secondly, consider the following:

```
sudo apt-get install kdelibs4-dev sWubversion unsermake automake1.9 kdebase-dev build-essential ruby ruby1.8-dev libtag1c2a libtag1-dev k3b libtunepimp5 libtunepimp5-mp3 libtunepimp-dev kdemultimedia kdemultimedia-dev libsdl1.2debian libsdl1.2-dev libvisual-0.4-0 libvisual-0.4-dev libvisual-0.4-plugins libgstreamer-plugins-base0.10-dev libxine-dev libfaad2-dev libgpod2 libgpod-dev
```

These take up over 300 Mb of disk space. Which of them can I safely remove afterwards?

Thanks again in principle though. I'm looking forward to getting some music on the Zen!

---

### Post by liveforfunnow on 2008-01-12
worked perfectly! i can now delete from and add to my ZEN in Ubuntu! Windows is a goner!

can Amarok do video? I didn't see a place for that. I'd like to be able to throw some DVD rips on the ZEN, but I don't know how in Ubuntu.

---

### Post by nmsmith on 2008-01-12
Well unfortunately I ended up in dependency hell, partly because I'm running 64-bit ubuntu I think.

Anyway, I got an error when trying to autodetect devices in amarok, and it would not connect to my device when I entered the details manually as you suggested.

Interestingly mtp-detect does produce useful data. Odd.

---

### Post by narehart on 2008-01-12
> worked perfectly! i can now delete from and add to my ZEN in Ubuntu! Windows is a goner!

can Amarok do video? I didn't see a place for that. I'd like to be able to throw some DVD rips on the ZEN, but I don't know how in Ubuntu.


I'm glad my guide worked for you.  As for video,  I'll probably be adding to this guide sometime next week to include a video HOW TO as well.  There's still a few bugs I have to work out.

---

### Post by narehart on 2008-01-12
> Thanks for this: I'm following the instructions as I write . . .

I have one question and one concern though.

You mention installing a bunch of libraries to enable ipod support and cd burning, but doesn't amarok have these in its native ubuntu .deb form?

The deb comes with ipod support enabled by default but not cd burning or ripping.  Those require K3B.  The difference between the deb and what we are doin here  is that your compiling Amarok yourself.  Any additional functionality that you want has to be enabled by you.  

> Secondly, consider the following:

Code:

sudo apt-get install kdelibs4-dev sWubversion unsermake automake1.9 kdebase-dev build-essential ruby ruby1.8-dev libtag1c2a libtag1-dev k3b libtunepimp5 libtunepimp5-mp3 libtunepimp-dev kdemultimedia kdemultimedia-dev libsdl1.2debian libsdl1.2-dev libvisual-0.4-0 libvisual-0.4-dev libvisual-0.4-plugins libgstreamer-plugins-base0.10-dev libxine-dev libfaad2-dev libgpod2 libgpod-dev

These take up over 300 Mb of disk space. Which of them can I safely remove afterwards?

Thanks again in principle though. I'm looking forward to getting some music on the Zen!

I guess I can tell you what each of these does and you can decide for yourself if you want them or not.  If you decide not to keep any of the packages remove the dev of it as well.

k3b - Amarok allows you to burn both audio and data CDs if K3B is installed. K3B is highly recommended, it makes burning CDs as easy as selecting tracks, right-clicking and selecting the burn option in the context-menu.

libtunepimp5 libtunepimp5-mp3 libtunepimp-dev - libtunepimp provides MusicBrainz support for Amarok. MusicBrainz allows you to do web lookups for track meta-data. This is a very helpful feature if your tracks are missing tags.

kdemultimedia kdemultimedia-dev - KDEmultimedia provides the audiocd:/ protocol that Amarok uses for ripping audio CDs.

libsdl1.2debian libsdl1.2-dev libvisual-0.4-0 libvisual-0.4-dev libvisual-0.4-plugins -  Libvisual gives Amarok eye-pleasing visualizations. 

libgpod2 libgpod-dev - libgpod provides Apple iPod support.

> Well unfortunately I ended up in dependency hell, partly because I'm running 64-bit ubuntu I think.

Anyway, I got an error when trying to autodetect devices in amarok, and it would not connect to my device when I entered the details manually as you suggested.

Interestingly mtp-detect does produce useful data. Odd.

Yeah, sorry I haven't tested this on 64-bit.  As for Amarok not detecting your device, did you install mtp-tools?

---

### Post by malcam on 2008-01-14
This worked very well thanks, you should make it clearer that people should run the .deb files as well as the command lines as I bet a lot of people will be missing those links. Now all I need is to find a way of getting the play counts to add to last.fm - like iPods do, I assumed these new Zens actually count the number of plays?

---

### Post by nmsmith on 2008-01-14
> **narehart said:**
> The deb comes with ipod support enabled by default but not cd burning or ripping.

Okay thanks, that makes sense. By that then do you mean that the other packages (e.g. K3B and kdemultimedia) are needed at compile time to give *persistent* functionality to amarok, or that they are required to remain present afterwards?

Thanks too for the breakdown of the packages: I could have read the output from aptitude show, but your descriptions are most helpful, and beyond the call of duty!

Being a Gnome user I'd like to be able top remove them if they provide duplicate functions to things like gnomad2, gnomebaker, serpentine and sound-juicer.

> **narehart said:**
> Yeah, sorry I haven't tested this on 64-bit.  As for Amarok not detecting your device, did you install mtp-tools?

Yes I did, hence the output from mtp-detect.

One other thing I did different to you (this may have been a really dumb move) was to get the amd64 versions of all the debian packages you linked to. Perhaps that was wrong.

I also have a further question: your howto seems to instruct compiling libmtp-0.2.4 (the latest version, that makes sense) and installing libmtp7 from the debian repos. Are these distinct from each other?

Thanks for your attention and kind help.

---

### Post by narehart on 2008-01-14
> This worked very well thanks, you should make it clearer that people should run the .deb files as well as the command lines as I bet a lot of people will be missing those links.

Good point.  I changed the wording of the instructions so that people would understand they were installing .deb files and made the text bold, just to be sure.

> Now all I need is to find a way of getting the play counts to add to last.fm - like iPods do, I assumed these new Zens actually count the number of plays?

Yes, I've checked the Zens do count the number of plays.  Coincidentally,  I have a mailing list topic with the libmtp team and the Amarok team to see if we can come up with a way to extract the play count, submit it to last.fm and clear the playcount back to zero before disconnecting.  Unfortunately,     I have very little C++ experience which is what would be required.  If you know anyone interested in contributing to this project please direct them to my post about the subject[ here]("http://ubuntuforums.org/showthread.php?t=664142").

> 
By that then do you mean that the other packages (e.g. K3B and kdemultimedia) are needed at compile time to give persistent functionality to amarok, or that they are required to remain present afterwards?

Being a Gnome user I'd like to be able to remove them if they provide duplicate functions to things like gnomad2, gnomebaker, serpentine and sound-juicer.

K3b and kdemultimedia have to remain even after the compiling and installation process are complete.  Amarok calls on K3b to burn and rip CDs and kdemultimedia tells it how to do that.

If you'd prefer to use those applications you don't have to compile Amarok at all.  You could just compile gnomad2 and transfer files that way.  It's not as intuitive or functional (IMO) as Amarok but it is an alternative.

Also, you could compile Rhythmbox from source and use your Zen with that if you really want to stick with GNOME applications.

> I also have a further question: your howto seems to instruct compiling libmtp-0.2.4 (the latest version, that makes sense) and installing libmtp7 from the debian repos. Are these distinct from each other?

Honestly, I am unsure whether these are distinct or not.  They both have the same version number but nowhere on the libmtp website is the latest version referred to as libmtp7 but of course this could just be the naming convention used by Debian for the package.

It's quite possible that there may be no need to compile libmtp but, this is the procedure that worked for me and it's relatively easy to do.

---

### Post by nmsmith on 2008-01-14
Well thanks. I tried again, and with a few issues it worked.

Primarily there is some sort of dependency problem. I can't work out why (as below) a dependency upon libc6-2.6 is not satisfied by having libc6-2.7 installed. Surely a more recent version is acceptable!

Anyway, here were the issues with installation (amd64 flavour ubuntu):

[LIST]
[*]I had to substitude the amd64 debs for the i386 ones you link to
[*]the bit where you say to install the big list of packages chucks out the dependency problems (see code tags below). I accepted the solutions, then reinstalled the debian debs again afterwards
[*]I am still left with the same dependency issue at the end, something to do I think with needing to have i386 libraries for a lot of things to work properly (e.g. flashplugin-nonfree)
[/LIST]

```
The following packages have unmet dependencies:
  libc6-i386: Depends: libc6 (= 2.6.1-1ubuntu9) but 2.7-5 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
libmtp-dev
libmtp7
mtp-tools

Upgrade the following packages:
libc6-i386 [2.6.1-1ubuntu9 (gutsy, now) -> 2.6.1-1ubuntu10 (gutsy-updates)]

Downgrade the following packages:
libc6 [2.7-5 (now) -> 2.6.1-1ubuntu10 (gutsy-updates)]
libc6-dev [2.7-5 (now) -> 2.6.1-1ubuntu10 (gutsy-updates)]

Score is 207

Accept this solution? [Y/n/q/?]
```

One suggestion I would have is to rearrange the order of the instructions to add the .deb packages after doing the apt-get installations. Mind you I think that's like trying to use WD-40 to fit a square peg into a round hole. Perhaps also you could provide a separate liest of links to the amd64 debs and a note to grab these instead for 64-bit users.

One other issue is when trying to copy or play files from my Zen into amarok, I get a popup from the lower left corner saying > Error Loading Media
No suitable input plugin. This often means that the url's protocol is not supported. Network failures are other possible causes.

The final issues, not related to your (greatly appreciated) howto, are that most of my music library is in the unsupported ogg format, and that I now have a hugely cluttered "Sound & Video" menu, not to mention a new program to learn!

I don't want to sound too down about my success: with your help I'm a million miles from where I started (player completely unsupported).

---

### Post by malcam on 2008-01-14
Edit - never mind, ignore this post as I was being stupid and forgot I was using the network drive - hence the network activity! ;)

---

### Post by narehart on 2008-01-15
> One suggestion I would have is to rearrange the order of the instructions to add the .deb packages after doing the apt-get installations.

Why do you suggest this?  Do you believe that the deb packages are interfering with apt-get installations? If so, can you point to, specifically, what leads you to this conclusion?

> Perhaps also you could provide a separate liest of links to the amd64 debs and a note to grab these instead for 64-bit users.

I'd be willing to do this if someone could test the installation procedure on a fresh install of a 64-bit system. Until then, no.  I'm against advising people to try things that I haven't done myself first.

> most of my music library is in the unsupported ogg format

Well, the only solutions to this are either converting them by installing sound converter or returning the Zen for something ogg compatible.  I think for my next player I will be looking for something like this.

> I now have a hugely cluttered "Sound & Video" menu

There are two solutions to this problem as well.  You could find the individual programs you don't want and uninstall them or, if you feel this may interfere with something, you could edit the menu so that they're not displayed.

> a new program to learn!

Amarok is an amazing music manager.  Once you've become familiar with it I'm sure you will love it.

---

### Post by nmsmith on 2008-01-15
> **narehart said:**
> Why do you suggest this?  Do you believe that the deb packages are interfering with apt-get installations? If so, can you point to, specifically, what leads you to this conclusion?

Well I'm not sure what's happening at the moment, so your reticence is well-advised!

> **narehart said:**
> I'd be willing to do this if someone could test the installation procedure on a fresh install of a 64-bit system. Until then, no.  I'm against advising people to try things that I haven't done myself first.

Whereas conversely my machine is a 24/7 MythTV server now on its third Ubuntu release, which is definitely not vanilla.

> **narehart said:**
> installing sound converter

Which I was doing when I discovered the dependencies weren't sorted! I intend to do this though. Oddly, my .m4a files leftover from iTunes also would not go onto the Zen, something about the device not supporting this file format.

I would love to be able to use Amarok - I've heard so much in the past - but more seems broken now than I can reasonably put up with.

A short list:
[LIST]
[*]my cdrom drive no longer seems to mount, although Amarok can play it (it finds it at cdda: though, not /media/cdrom)
[*]Amarok does not get CD track names (perhaps the ripping function didn't make it through the compile)
[*]the music library is only viewable from my own user account, not from any other
[*]Amarok frequently exits with a complaint about not being able to find kmail for bug notification
[*]dependency issues already mentioned
[*]the problem with not being able to copy tracks from the Zen to the library
[/LIST]

My earlier suggestions about the .debs were just that: suggestions, but I have a better one for now I'm afraid to admit . . . my own "here be dragons" about doing this on non vanilla 64-bit!

I think I may bail out and wait to see whether Hardy carries a newer libmtp.

---

### Post by narehart on 2008-01-15
> 
    * my cdrom drive no longer seems to mount, although Amarok can play it (it finds it at cdda:    
      though, not /media/cdrom)
    * Amarok does not get CD track names (perhaps the ripping function didn't make it through the 
      compile)
    * the music library is only viewable from my own user account, not from any other
    * Amarok frequently exits with a complaint about not being able to find kmail for bug notification
    * dependency issues already mentioned
    * the problem with not being able to copy tracks from the Zen to the library


I'm sorry that your having numerous issues.  I have a 64 bit capable machine but am not currently able to reinstall to experiment and help resolve your issues.  I don't know if your aware, but you can install the 32 bit version of Ubuntu on your operating system.

> 
I think I may bail out and wait to see whether Hardy carries a newer libmtp.

Hardy does carry the new libmtp and I've read on another post of someones Zen working right away but the OS itself is highly unstable. If your in the market for a new operating system PClinuxOS is very nice and has the new libmtp already installed.

Sorry this didn't pan out for you.  I'm going to put a warning in the original post to 64 bit users.  Feel free to contact me if you have any more questions.

---

### Post by Sciamano on 2008-01-19
I followed the guide but have these problems:

- Amarok freezes immediately after launching. It shows up, but the freezes.
- I've installed mtp-tools from your link, but if I launch 'mtp-tools' in the terminal I get:

```
bash: mtp-tools: command not found
```

still if I check Adept, I can see version 0.2.4-5 installed.

---

### Post by narehart on 2008-01-20
> - Amarok freezes immediately after launching. It shows up, but the freezes.
- I've installed mtp-tools from your link, but if I launch 'mtp-tools' in the terminal I get:


Run Amarok from the terminal and post the output.

---

### Post by Sciamano on 2008-01-20
> **narehart said:**
> Run Amarok from the terminal and post the output.

I can't, because I tried to revert to the original setup and...

This is a **[COLOR="Red"]_[SIZE="3"]WARNING[/SIZE]_[/COLOR]** for everybody: 

**ask** for instructions if you want to "uninstall" all this procedure because when I tried, apt-get basically uninstalled my whole Kubuntu!
I had to reinstall the system from scratch to make it work again, so don't make my same mistake and **BE CAREFUL**!

---

### Post by Seamyst on 2008-01-22
Wow.... it worked!  I followed the instructions exactly (except my Zen was plugged in) and ended up with problems - Amarok didn't install properly and there were dependency errors.  So I unplugged the Zen, uninstalled everything, and took it from the top.  This time it worked!  I swear I followed the instructions exactly the same both times, so the only thing I can figure is that the Zen is NOT supposed to be plugged in during all this.

Maybe it's just really obvious to everyone else... but perhaps you could put a note saying as much at the top?

---

### Post by narehart on 2008-01-23
> **Seamyst said:**
> Wow.... it worked!  I followed the instructions exactly (except my Zen was plugged in) and ended up with problems - Amarok didn't install properly and there were dependency errors.  So I unplugged the Zen, uninstalled everything, and took it from the top.  This time it worked!  I swear I followed the instructions exactly the same both times, so the only thing I can figure is that the Zen is NOT supposed to be plugged in during all this.

Maybe it's just really obvious to everyone else... but perhaps you could put a note saying as much at the top?

Yeah, that makes sense.  If libmtp isn't installed the system manages the Zen as a usb device.

---

### Post by Noljevic on 2008-01-31
I've a problem,
when I try to install the deb package libc6, I can't found it on the link and then it's impossible to continue. How I can solve it?

Thanks.

---

### Post by TimJ on 2008-02-01
Thanks a million for the guide. I used it and got my zen working. I had to do a few things differently and just in case it helps anyone else here's the three things not in the guide I had to do.

First, I had to have a Ubuntu 7.10 cd in my cdrom drive.
Second, all the links for libc6, libmtp7, libc6-dev etc that occur about half way just before you configure libmtp are broken. I installed all of them using Synaptic Package Manager EXCEPT for libmtp7 which Synaptic didn't have. I didn't install libmtp7. I installed libmtp-tools from synaptic as well.
Third, I had to start Amarok using /sudo amarok in a terminal to get it to connect. Once I did that it was fine.

Thanks again, I'd never have gotten it working without your guide.

---

### Post by teh_lam3 on 2008-02-10
same problem as previous poster the deb is gone and when i try and install libc6_2.7-6_i386.deb it conflicts with tzdata ******* dependecy hell :(

---

### Post by Sciamano on 2008-02-10
I don't get the need to compile Amarok.
It should work even without this step.

---

### Post by Noljevic on 2008-02-12
I've the same problem like teh_lam3. I tried a lot of things to solve this error depency with tzdata and with deb packages but I couldn' :(. Can someone help us, please?

---

### Post by narehart on 2008-02-12
sorry debian must have updated the packages. google libc6 and install it from the debian site along with any dependencies,

---

### Post by sfabel on 2008-02-18
Thank you for the guide. I have a couple of questions before I follow it, though.

Is there no way around recompiling amarok?

When I try to remove libmtp,it wants to uninstall Amarok. Wouldn't installing a new version of libmtp from source and the removing the libmtp.so.6 from /usr/lib work just as well? Or is there a sane way to "force remove" a debian package deliberately leaving dependencies open?

Last, is there no way to just provide the debs in a ppa for us?

Thanks,
Stephan

---

### Post by Sciamano on 2008-02-19
You can remove all instances of libmtp.so.6 (don't use apt-get, just locate them and then delete them by hand), then replace them by creating symbolic links that point to the libmtp.so.7 you compiled from source.
It's not an orthodox solution but it worked for me.

---

### Post by sternkanz on 2008-02-26
I'm also trying to get my zen to work on my gutsy machine. I followed your guide and everything worked fine until I need to install libc6. I can't install it because it says:

Error: Conflicts with the installed package 'tzdata'

And from there I can't install any of the other packages because they're all dependant on libc6. Is there something I can do?

Thanks!

Stern

---

### Post by narehart on 2008-02-28
I've recently had to reinstall my system and in turn, get my Zen working again.  I've found a quicker and easier way to do this.
[B][COLOR="Red"]
NOTE: DO NOT UPDATE YOUR SYSTEM AT ANYTIME DURING THIS PROCESS![/COLOR][/B]

All that needs to be done is to uninstall libmtp6 and amarok via Synaptic. 

Then add the Hardy repository:

```

sudo gedit /etc/apt/sources.list

```

```
##Hardy##
deb http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse

```

Open Synaptic. search for libmtp7, Amarok and mtp-tools and install.

Remove the Hardy repository:

```

sudo gedit /etc/apt/sources.list

```

Delete this line:

```
##Hardy##
deb http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse

```

This is MUCH easier and installs all dependencies automatically

---

### Post by Sciamano on 2008-02-29
> **narehart said:**
> All that needs to be done is to uninstall libmtp6 and amarok via Synaptic. 

Then add the Hardy repository:
[......]
This is MUCH easier and installs all dependencies automatically

Yes it might be easier but Linux gurus always warn not to do such a thing...
Something related to broken dependencies, don't know exactly what it is.
I still don't understand why you can't simply update libmtp to the latest version, which is the safest solution...

---

### Post by narehart on 2008-02-29
I understand the inherent danger in this and if your inexperienced I don't recommend this but the only risk involved really is if you update your system.  As long as you remove the the Hardy source you shouldn't experience any problems.

---

### Post by thedaylights on 2008-03-16
EDIT: Originally I had the following problems.

> I followed these directions but when I configure an MTP device in Amarok I get an error. After clicking okay or apply on the preferences window, a dialog opens about failure to launch kmail. I'm guessing it's an automatic response to file a bug report. What can I do to get my Zen working on Amarok?

Perhaps I should mention that several of the links in your tutorial were dead, so I used apt-get install instead. And often the results of that were "you already have the latest version".

Note, my Amarok library is also dead now. I can play songs with random playlist, but clicking on collection shows no songs at all.

EDIT: I removed Amarok and reinstalled it, figuring I could fix some dependency issues. It didn't work at first, but then after Ubuntu did a few updates it is now working like a charm.

---

### Post by genialself on 2008-03-29
I have a Creative Zen 8GB mp3 player.  I have followed this HOW-To and have run into a couple problems.  This first one is quite minor, the direct links in the HOW-TO need to be updated.  The packages they point to are no longer available but have been replaced by newer versions. The versions I installed are as follows:

libc6_2.7-9_i386.deb
libmtp7_0.2.6.1-1_i386.deb
libc6-dev_2.7-9_i386.deb
libusb-0.1-2_0.1.12-9_i386.deb
libusb-dev_0.1-2_0.1.12-9_i386.deb
libmtp-dev_0.2.6.1-1_i386.deb
mtp-tools_0.2.6.1-1_i386.deb

All of the above installed with no errors or problems.

The second problem has me stumped.  Everything installed with no problems but I can't see my Zen. The lsusb command shows it as connected and the relevant output of /proc/bus/usb/devices is shown here:

T:  Bus=05 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#= 18 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=041e ProdID=4157 Rev= 1.00
S:  Manufacturer=Creative Technology Ltd
S:  Product=Creative ZEN
S:  SerialNumber=XXXXXXXXXXXXXXXXXXXXX
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=500mA
I:* If#= 0 Alt= 0 #EPs= 3 Cls=00(>ifc ) Sub=00 Prot=00 Driver=(none)
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=4096ms

As you can see the driver is listed as (none).  I cannot find this product ID listed anywhere by googling.   Where can I find, and how do I assign, a driver for this device?
The creative website does have some linux related drivers, etc. but has nothing for this device.

Any help is greatly appreciated.   Thanks

---

### Post by JollyJu on 2008-03-31
Love ya, just love ya for this!!!!!!!!  ...;)

---

### Post by lune on 2008-04-03
> **narehart said:**
> I've recently had to reinstall my system and in turn, get my Zen working again.  I've found a quicker and easier way to do this.
[B][COLOR="Red"]
NOTE: DO NOT UPDATE YOUR SYSTEM AT ANYTIME DURING THIS PROCESS![/COLOR][/B]

All that needs to be done is to uninstall libmtp6 and amarok via Synaptic. 

Then add the Hardy repository:

```

sudo gedit /etc/apt/sources.list

```

```
##Hardy##
deb http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse

```

Open Synaptic. search for libmtp7, Amarok and mtp-tools and install.

Remove the Hardy repository:

```

sudo gedit /etc/apt/sources.list

```

Delete this line:

```
##Hardy##
deb http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse

```

This is MUCH easier and installs all dependencies automatically

Just followed these instructions on Gutsy 64-bit and I can now transfer files to/from my Zen.

---

### Post by anthony.phipps on 2008-04-18
new links are out for this section in the original post:
> Click on the following links and install the .deb packages:

libc6 libmtp7 libc6-dev libusb-0.1-4 libusb-dev libmtp-dev

they are as follows, in sequential order:
[http://http.us.debian.org/debian/pool/main/g/glibc/libc6_2.7-10_i386.deb](http://http.us.debian.org/debian/pool/main/g/glibc/libc6_2.7-10_i386.deb)
[http://http.us.debian.org/debian/pool/main/libm/libmtp/libmtp7_0.2.6.1-2_i386.deb](http://http.us.debian.org/debian/pool/main/libm/libmtp/libmtp7_0.2.6.1-2_i386.deb)
[http://http.us.debian.org/debian/pool/main/g/glibc/libc6-dev_2.7-10_i386.deb](http://http.us.debian.org/debian/pool/main/g/glibc/libc6-dev_2.7-10_i386.deb)
[http://http.us.debian.org/debian/pool/main/libu/libusb/libusb-0.1-4_0.1.12-10_i386.deb](http://http.us.debian.org/debian/pool/main/libu/libusb/libusb-0.1-4_0.1.12-10_i386.deb)
[http://http.us.debian.org/debian/pool/main/libu/libusb/libusb-dev_0.1.12-10_i386.deb](http://http.us.debian.org/debian/pool/main/libu/libusb/libusb-dev_0.1.12-10_i386.deb)
[http://http.us.debian.org/debian/pool/main/libm/libmtp/libmtp-dev_0.2.6.1-2_i386.deb](http://http.us.debian.org/debian/pool/main/libm/libmtp/libmtp-dev_0.2.6.1-2_i386.deb)

---

### Post by Seamyst on 2008-05-07
> **narehart said:**
> I've recently had to reinstall my system and in turn, get my Zen working again.  I've found a quicker and easier way to do this.
[B][COLOR="Red"]
NOTE: DO NOT UPDATE YOUR SYSTEM AT ANYTIME DURING THIS PROCESS![/COLOR][/B]
[.....]
This is MUCH easier and installs all dependencies automatically

Yes!  I finally got Amarok to read my Zen with these instructions.  Thank you!

---

### Post by AnthonyHorner on 2008-05-28
Hi,

I'm having trouble installing the development files in the step before installing amarok (using Hardy Heron).  The message that comes back is the following:

anthony@anthony-laptop:~/libmtp/libmtp-0.2.4$ sudo apt-get install kdelibs4-dev subversion unsermake automake1.9 kdebase-dev build-essential ruby ruby1.8-dev libtag1c2a libtag1-dev k3b libtunepimp5 libtunepimp5-mp3 libtunepimp-dev kdemultimedia kdemultimedia-dev libsdl1.2debian libsdl1.2-dev libvisual-0.4-0 libvisual-0.4-dev libvisual-0.4-plugins libgstreamer-plugins-base0.10-dev libxine-dev libfaad2-dev libgpod2 libgpod-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package unsermake
anthony@anthony-laptop:~/libmtp/libmtp-0.2.4$ 


Please help!

Anthony

---

### Post by pimpff on 2008-05-30
Hi @ all,

this is my first post at this forum.

Thank you, narehart, for your how-to. It was very helpfull. Now, after a few weeks of using my Zen on Windows, I can connect it with Amarok, but...
Deleting old mp3-tracks on the Zen: no problem.
When I try to transfer new songs with complete ID3-tags to the device, they apear only by the name of the artist in the quee before transfer.
Therefor, there are no differencies in the names of the files.

Example:
AC-DC - Who made who - Ride On 
is taken as:
AC-DC -

My first though: Wow, Amarok is realy fast, great, the bad awakening came afterwards.

Can anybody help me with the Amarok-settings of my Zen?

Thank you!
Jan

---

### Post by AnthonyHorner on 2008-05-30
Hi again,

Been slowing finding my way (like two days trying to get a synch with my pda for starters!)  Can anybody confirm that I need to have the kde installed on ubuntu then to be able to be able to do follow the steps outlined in the first post?  

If that is the case, I&#314;l have to uninstall gnome (plus my gnome-pilot sniff, sniff)


Edit:  Found workaround to my problem, just deleted unsermake from the command line and it uses automake command

---

### Post by Auslegung on 2008-06-24
> **anthony.phipps said:**
> new links are out for this section in the original post:


they are as follows, in sequential order:
[http://http.us.debian.org/debian/pool/main/g/glibc/libc6_2.7-10_i386.deb](http://http.us.debian.org/debian/pool/main/g/glibc/libc6_2.7-10_i386.deb)
[http://http.us.debian.org/debian/pool/main/libm/libmtp/libmtp7_0.2.6.1-2_i386.deb](http://http.us.debian.org/debian/pool/main/libm/libmtp/libmtp7_0.2.6.1-2_i386.deb)
[http://http.us.debian.org/debian/pool/main/g/glibc/libc6-dev_2.7-10_i386.deb](http://http.us.debian.org/debian/pool/main/g/glibc/libc6-dev_2.7-10_i386.deb)
[http://http.us.debian.org/debian/pool/main/libu/libusb/libusb-0.1-4_0.1.12-10_i386.deb](http://http.us.debian.org/debian/pool/main/libu/libusb/libusb-0.1-4_0.1.12-10_i386.deb)
[http://http.us.debian.org/debian/pool/main/libu/libusb/libusb-dev_0.1.12-10_i386.deb](http://http.us.debian.org/debian/pool/main/libu/libusb/libusb-dev_0.1.12-10_i386.deb)
[http://http.us.debian.org/debian/pool/main/libm/libmtp/libmtp-dev_0.2.6.1-2_i386.deb](http://http.us.debian.org/debian/pool/main/libm/libmtp/libmtp-dev_0.2.6.1-2_i386.deb)

From what I can tell, these are the links for #4 and #5 that are now broken:

[[COLOR="Blue"]http://http.us.debian.org/debian/pool/main/libu/libusb/libusb-0.1-4_0.1.12-11_i386.deb[/COLOR]]("http://http.us.debian.org/debian/pool/main/libu/libusb/libusb-0.1-4_0.1.12-11_i386.deb")

[[COLOR="Blue"]http.us.debian.org/debian/pool/main/libu/libusb/libusb-dev_0.1.12-11_i386.deb[/COLOR]]("http.us.debian.org/debian/pool/main/libu/libusb/libusb-dev_0.1.12-11_i386.deb")

I'm not 100% sure, but that's what it looks like.

---

### Post by Auslegung on 2008-06-24
> **AnthonyHorner said:**
> Hi again,

Been slowing finding my way (like two days trying to get a synch with my pda for starters!)  Can anybody confirm that I need to have the kde installed on ubuntu then to be able to be able to do follow the steps outlined in the first post?  

If that is the case, I&#314;l have to uninstall gnome (plus my gnome-pilot sniff, sniff)


Edit:  Found workaround to my problem, just deleted unsermake from the command line and it uses automake command

Had the same problem, and also had 

Package libfaad2-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libfaad-dev
E: Package libfaad2-dev has no installation candidate

and 

Package libgpod2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgpod2 has no installation candidate


I left those out and when I got to the end my Zen didn't mount.  Don't know what exactly the problem is b/c I was forced to make so many changes from his original how-to.

PS: Here's what I think the link is for the mtp tools:

[[COLOR="Blue"]http://http.us.debian.org/debian/pool/main/libm/libmtp/mtp-tools_0.2.6.1-2_i386.deb[/COLOR]]("http://http.us.debian.org/debian/pool/main/libm/libmtp/mtp-tools_0.2.6.1-2_i386.deb")

---

### Post by milan_cortana on 2008-07-18
Hi all
After trying command:sudo apt-get remove libmtp6 libmtp-dev libmtp-doc
J got this:E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Can someone help me please?

thanks 

Milan

---

### Post by sfabel on 2008-07-19
> 
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


That says it all... do you have Synaptic, Adept or another apt-get process running? If you don't know how to find that out, a reboot should do. Another possibility could be that the Update Manager was updating in the background when you tried that command.

Cheers,
Stephan

---


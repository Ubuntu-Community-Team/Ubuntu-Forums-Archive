---
title: "[HOW-TO] Sansa View in MTP Mode"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by sdyson on 2007-12-28
Got a SanDisk Sansa View for Christmas. It's a lovely little MP3 player but it was a bit cumbersome to put it into the hidden MSC mode to put music on it so I've figured out how to get MTP mode to work. This is to get it working using Gutsy Gibbon but it should act as a good starting point for other Ubuntu releases or MTP MP3 players. 

First of all this uses a library called libmtp. The version in the Gutsy Gibbon repositories is 0.2.1 and does not work with the Sansa View. Unless you can find an alternative repository you're going to need to build this yourself. Download the latest version from [http://libmtp.sourceforge.net](http://libmtp.sourceforge.net) (I got 0.2.4) and unpack the archive. Then in a console cd to the directory you just unpacked and run the following 3 commands:

```

./configure
sudo make
sudo make install

```
Next you need to edit /etc/udev/rules.d/libmtp.rules in your favourite editor and add the Sansa View to the list of devices as follows. Notice the MODE is 666 to ensure your own user has access to the device. You will need to restart for these changes to take effect.

```

# SanDisk Sansa View
ATTRS{idVendor}=="0781", ATTRS{idProduct}=="74b0", SYMLINK+="libmtp-%k", MODE="666", GROUP="audio"

```
Now we want to make sure everything is working so you want to install mtp-tools using the package manager or as follows:

```

sudo apt-get install mtp-tools

```
Connect the Sansa View to the PC using the supplied cable and then run the following command:

```

mtp-detect

```
This will detect any available MTP devices and print out lots of information about the View if successful. If you get any errors make sure you are using the correct version of libmtp - the first thing mtp-detect prints out is the libmtp version. 

At this stage you should be able to use the View as an MTP device using your preferred media application. I use Amarok which is packaged with MTP support in Gutsy Gibbon. All you need to do is go to 'Media Devices' in the configuration dialog and add an 'MTP Media Device', then press the connect button on the 'Devices' view.

---

### Post by kevinlang21 on 2008-01-20
Does it matter where you unpack it to? Gutsy already has an older version of libmtp.

---

### Post by kevinlang21 on 2008-01-20
i get this error message:

> kevin@computer:/opt/libmtp-0.2.4$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.


:( can you help me please?

---

### Post by sdyson on 2008-01-21
I changed the configure command to not specify a prefix. Should install to default Ubuntu location. 

Have you tried the following:

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by the_master on 2008-01-24
> **sdyson said:**
> I changed the configure command to not specify a prefix. Should install to default Ubuntu location. 

Have you tried the following:

```
sudo aptitude update
sudo aptitude install build-essential
```

Thank you that did work but now i have a different error

```
configure: error: I can't find the libusb libraries on your system. You
        may need to set the LDFLAGS environment variable to include the
        search path where you have libusb installed before running
        configure (e.g. setenv LDFLAGS=-L/usr/local/lib)

```

I´ll try to fix it, if i do i´ll post the solution.

EDIT:
FIgured out that error
you will need the library libusb-dev
```
sudo apt-get install libusb-dev
```
I then got to mtp-detect and i get this error
```
mtp-detect: error while loading shared libraries: libmtp.so.7: cannot open shared object file: No such file or directory

```
Once again if i figure it out i will post the problem

---

### Post by sdyson on 2008-01-24
the_master, since you had to install libusb I'm guessing you hadn't previously installed libmtp 0.2.1 from the repositories. You could try that and then install libmtp 0.2.4 over the top  - see if that fixes your problem.

---

### Post by Sciamano on 2008-02-02
> **the_master said:**
> 
```
mtp-detect: error while loading shared libraries: libmtp.so.7: cannot open shared object file: No such file or directory

```
Once again if i figure it out i will post the problem

Did you figure it out? I'm having the same problem, but anything I've tried has failed

---

### Post by coaltown on 2008-02-18
> 
```
mtp-detect: error while loading shared libraries: libmtp.so.7: cannot open shared object file: No such file or directory

```

Once again if i figure it out i will post the problem

In my case the linker was looking for /usr/lib/limtp.so.7. There are two ways to appease the linker. Either edit /etc/ld.so.conf and add the following line:

include /usr/lib

or make a symbolic link from /usr/local/lib/libmtp.so.7 to /usr/lib/libmtp.so.7 with the following commands:

```
cd /usr/lib
sudo ln -s /usr/local/lib/libmtp.so.7 libmtp.so.7
```
I chose the latter option and it worked like a charm

---

### Post by Sciamano on 2008-02-18
I gave the command:

```
sudo ldconfig
```

and it solved the shared libraries problem.

---

### Post by BostonAdvocat on 2008-02-24
Thank you for the excellent write up. It worked for me with some differences. 

**My Setup**
[LIST]
[*]Kubuntu 7.04 (Feisty Fawn)
[*]Amarok 1.4.7 Music player (latest release)
[*]Sansa View 16 GB (firmware according to 'mtp-detect': 01.02.09A)
[/LIST]

The first thing I did when I got it a few days ago was update to the latest firware, 1.02.09 on 2/23/08. I was using it in MSC mode in Amarok 1.4.5 and it successfully transfered songs. However, there were plenty of minor problems when playing the mp3's when transferring in MSC mode. What was frustrating was that this was inconsistent even between songs on the same album. One song would display correctly under a given album, but another song from the same album wouldn't display. It would show up under the "Unknown Album". Some careful double checking confirmed this. This and other problems listed below affected some mp3s, but not others. As for the album art, all the art was embedded within the mp3 files, not as JPGs within folders. I prefer to keep the art embedded within the files for better maintainability.

[B]
Problems with MSC under Kubuntu 7.04 Linux[/B]
[LIST]
[*]Artist name was unknown
[*]Album title was unknown
[*]Album art missing
[/LIST]

My best guess after eliminating common possibilities is that the player can only read certain versions of ID3v2. There are multiple versions of ID3v2 and because these mp3's come from so many different sources it's likely that there's great variance in versions even within a single album. THIS CAN BE FIXED using EasyTAG to harmonize all your mp3s into a single version. Rather than try that, however, I attempted to try connecting via MTP mode. It does in fact work. You need to follow the poster's instructions carefully. And unlike the aforementioned problems, MTP synchronization syncs all the information without any problems. It did cause Amarok to freeze up a few times when syncing more than a few songs, but after terminating the app, the songs it turns out did make it to the player.

The one problem I had with MTP after getting everything installed was with Amarok not finding the player. First off, I want to say that even though MTP synchronization works for my Sansa View, the device does not show up on my system as any kind of attached device. Running
```
ls /dev/sd*
```
doesn't yield anything other than my existing hard drives. Same for 
```
ls /dev/hd*
```

In order to get Amarok to recognize the device, I had to run 
```
mtp-detect
```
from the command line first. For this to be acceptable on a daily basis, Amarok does allow you to specify pre-connect commands on a per-device basis. That's great. 

Here's how you add your MTP device to Amarok. Open Amarok and go to 
[LIST=1]
[*]Settings -> Media Devices -> Add Device ...
[*]In the drop down, select "MTP Media Device"
[*]In the text box labeled "Enter a name for this device" give it a name like "Sansa View"
[*]Leave the bottom field blank. You will not provide a mount point.
[*]Click OK
[/LIST]

The device should now be listed under Media Devices. The the right of the combo box for the Sansa media device is a button with an icon of 3 gears. Click on this to configure your media device. 

In the first text box labeled "Pre-Connect command" enter "mtp-detect".
Click OK

Amarok will now run the command each time you try to connect to the device. For me, this is necessary in order for Amarok to see it. Otherwise it gives me an error stating that there is no MTP device connected to my computer. 

Here's the problem for me (anyone else getting this?): Amarok doesn't remember the pre-connect command. A couple of times, right after I enter it and click OK, I can go right back in and the text box is blank. Other times command disappeared only after closing Amarok.  Perhaps this is an unknown bug or just specific to my system. In any case, every morning when I plug in my View to download the latest podcasts, I'll have to re-enter the pre-connect command. Lucky for me, I rarely reboot my computer so Amarok is always open and in my system tray. If this isn't resolved, then if the aforementioned MSC related problems are resolved, I'll switch back to MSC mode.

Here's my personal blog post for more information:
[http://www.jozefnagy.com/?q=node/61](http://www.jozefnagy.com/?q=node/61)

---

### Post by Sciamano on 2008-02-25
> **BostonAdvocat said:**
> 

[B]
Problems with MSC under Kubuntu 7.04 Linux[/B]
[LIST]
[*]Artist name was unknown
[*]Album title was unknown
[*]Album art missing
[/LIST]


This never happened to me using MSC. Are you sure you copied the mp3 files to the MUSIC directory of the View?

> **BostonAdvocat said:**
> 
In order to get Amarok to recognize the device, I had to run 
```
mtp-detect
```
from the command line first. For this to be acceptable on a daily basis, Amarok does allow you to specify pre-connect commands on a per-device basis. That's great. 

That's what happens to me too (on Kubuntu 7.10), although I sometimes have to send the mtp-detect command more than once. Most of the times, as soon as I send my "first" mtp-detect, the View reboots. I have to send the command at the exact moment when the booting splash screen (the black one saying "Sandisk Sansa") disappears, and the main menu shows up. Immediately after that the black screen with the "connecting" writing shows up, and it's too late to send the mtp-connect. If I do that, the View reboots again.
Anyone else experiencing this problem?

---

### Post by BostonAdvocat on 2008-02-25
> **Sciamano said:**
> This never happened to me using MSC. Are you sure you copied the mp3 files to the MUSIC directory of the View?



That's what happens to me too (on Kubuntu 7.10), although I sometimes have to send the mtp-detect command more than once. Most of the times, as soon as I send my "first" mtp-detect, the View reboots. I have to send the command at the exact moment when the booting splash screen (the black one saying "Sandisk Sansa") disappears, and the main menu shows up. Immediately after that the black screen with the "connecting" writing shows up, and it's too late to send the mtp-connect. If I do that, the View reboots again.
Anyone else experiencing this problem?

Before synchronizing songs onto the View, Amarok was configured to put all the music into the MUSIC directory. That would be pretty bad if I was misplacing the music elsewhere so that couldn't be the cause of the problem. The aforementioned inconsistencies between songs on the same album happened even when I saw that the songs were in fact in the same sub-folder within MUSIC too. 

As for the mtp-detect command, I don't care that Amarok has to execute it in order to connect because after an initial configuration, it should be seamless. But the fact that Amarok tends to "forget" is irritating beyond the pale.

---

### Post by Sciamano on 2008-02-25
> **BostonAdvocat said:**
> Before synchronizing songs onto the View, Amarok was configured to put all the music into the MUSIC directory. That would be pretty bad if I was misplacing the music elsewhere so that couldn't be the cause of the problem. The aforementioned inconsistencies between songs on the same album happened even when I saw that the songs were in fact in the same sub-folder within MUSIC too. 

Considering that I've never experienced such problems, I can only suggest you check all your id3 tags. I'm very precise in setting id3 tags, and I've never had a file showing up as "unknown" on my Sansa View. If you are positive your id3 tags are ALL correctly set up, there must be something wrong in the transfer. I've noticed in the past that songs show up as unknown/unknown only when they are managed like "normal" files and not music tracks.

Anyway, you might also want to try [Qlix]("http://qlix.berlios.de/?page_id=6"). The latest SVN version works pretty well with the View in MTP mode (it's not perfect but very usable, if you can stand the occasional crash): I've been working personally with the programmer to solve some problems, and so far it's the best program I've found. It even manages covers correctly.

> **BostonAdvocat said:**
> As for the mtp-detect command, I don't care that Amarok has to execute it in order to connect because after an initial configuration, it should be seamless. But the fact that Amarok tends to "forget" is irritating beyond the pale.

I've never tried your method, because I've been using Qlix for managing my View since I've discovered this program. It's way lighter than Amarok, and IMHO does a better job (you can also transfer videos and pictures, while Amarok won't do it), especially with the cover art.

---

### Post by sdyson on 2008-02-25
You're correct about ID3v2 tags. It seems to be a problem that affects a lot of players including my Walkman phone. The solution is to ensure all your tags are ID3v2.3 and not v2.4. I found Picard the best tool for doing this over a largish collection.

---

### Post by leetcharmer on 2008-02-28
> **BostonAdvocat said:**
> 
Here's how you add your MTP device to Amarok. Open Amarok and go to 
[LIST=1]
[*]Settings -> Media Devices -> Add Device ...
[*]In the drop down, select "MTP Media Device"
[*]In the text box labeled "Enter a name for this device" give it a name like "Sansa View"
[*]Leave the bottom field blank. You will not provide a mount point.
[*]Click OK
[/LIST]

The device should now be listed under Media Devices. The the right of the combo box for the Sansa media device is a button with an icon of 3 gears. Click on this to configure your media device. 

In the first text box labeled "Pre-Connect command" enter "mtp-detect".
Click OK

Amarok will now run the command each time you try to connect to the device. For me, this is necessary in order for Amarok to see it. Otherwise it gives me an error stating that there is no MTP device connected to my computer. 

I followed all the steps for my Sansa Connect -- and when I do mtp-detect in the terminal, I get a buncha output -- so it appears as if it works.  But when I try to detect in Amarok, the connection always fails, and when I do mtp-detect in terminal after that, it output any data until I unplug and replug the device.

Any ideas why this is happening?

---

### Post by leetcharmer on 2008-02-28
actually -- after installing the mtp plugin with Rhythmbox, the device pops up with the application upon connection :D!  How convenient!  Then I just drag my Music onto the Sansa Connect and BAM we're in!

---

### Post by tehquickness on 2008-02-29
I am getting nothing after trying this. My question is, there is currently already a libmtp installed. Do we need to remove this? Do they conflict at all? Just wondering. I will post somethings later to help figure out this problem.

Thanks

---

### Post by Sciamano on 2008-02-29
> **tehquickness said:**
> I am getting nothing after trying this. My question is, there is currently already a libmtp installed. Do we need to remove this? Do they conflict at all? Just wondering. I will post somethings later to help figure out this problem.

Thanks

What do you mean with "getting nothing"?
What's the output of "mtp-detect"?

Regarding the other question: removing the installed libmtp from aptitude would create problems, because Amarok and other programs need this library. You can delete the shared libraries by hand, though. It should be named something like "libmtp.so.6".
I suggest you launch a "locate libmtp.so": you should find a few files by that name (like libmtp.so, libmtp.so.6 and libmtp.so.7) in /usr/lib
Delete them by hand and then replace them (using the same names of the deleted libraries) with symbolic links that point to the libmtp that you have compiled (should be libmtp.so.7, or 7.0.1... you get the idea... by default it gets installed in /usr/local/lib)
This way Amarok and the other programs that need libmtp.so.6 (because they've been compiled against them) will continue to work, using the latest version, though.

It's not an orthodox solution, but it works.

---

### Post by jonamoen on 2008-03-24
Thank you, thank you, thank you, thank you, thank you, thank you, thank you, thank you, thank you, thank you, thank you. Works like a charm. :)

---

### Post by snakep on 2008-04-21
> **coaltown said:**
> In my case the linker was looking for /usr/lib/limtp.so.7. There are two ways to appease the linker. Either edit /etc/ld.so.conf and add the following line:

include /usr/lib

or make a symbolic link from /usr/local/lib/libmtp.so.7 to /usr/lib/libmtp.so.7 with the following commands:

```
cd /usr/lib
sudo ln -s /usr/local/lib/libmtp.so.7 libmtp.so.7
```
I chose the latter option and it worked like a charm

I followed all the same steps, including installing mtp-tools and creating the symbolic link to get mtp-detect to work.  Now I am getting an error when I plug in my Sansa View:

```

libmtp version: 0.2.6.1

Attempting to connect device(s)
usb_claim_interface(): Operation not permitted
LIBMTP PANIC: Unable to initialize device 1
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1599
Detect: There has been an error connecting. Exiting

```

Anybody know what this means?  Is it a bug in libmtp?

Thanks,

Jeremiah

---


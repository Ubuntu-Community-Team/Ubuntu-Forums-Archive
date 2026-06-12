---
title: "nvidia settings can't save to conf file"
date: 2009-03-20
forum: Hardware
---

### Post by xkaliburx on 2009-03-20
ok, running nvidia settings (sudo nvidia-settings).  Using the newest 180 version drivers.  I have  an external monitor plugged in, but when I select it, select seperate X view, then the 'save to x' button I get the following;

Failed to parse existing X config file '/etc/X11/xorg.conf'!

Behind in the terminal screen I see;
ALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

Any ideas what could cause this?  Nothing has been modified by hand, and teh xorg is actually a tiny basic file shown below;

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Thanks

---

### Post by scottac on 2009-03-20
I had a similar problem a while back. try this if you havent already

```
sudo nvidia-settings
```

let me know how it goes

---

### Post by xkaliburx on 2009-03-20
1st line I typed!

> ok, running nvidia settings (sudo nvidia-settings). 

So that didn't do it.  As the post also stated, > Failed to parse existing X config file '/etc/X11/xorg.conf' is the error in the terminal screen.

So it's really not a permission thing but something with the xorg.conf file layout which is why I posted it.  It seems very small, but I haven't touched these files since the mid fedora day's.

Thanks

---

### Post by norwoods on 2009-03-21
run sudo nvidia-xconfig to create a new Xorg.conf.

if there is a problem with this, rename Xorg.conf and run sudo nvidia-xconfig.

---

### Post by Jæd on 2009-04-19
Was this solved...? I had this and in the end I copied and pasted the file contents displayed when the "Preview" button was pressed.

---

### Post by rgravenor on 2009-04-19
Hello!  I have the same issue.  I am trying to run two monitors in twinview off a single nvidia card.  I can it up to work beautifully using NVidia X server settings, but when i try to save it, it tells me "Failed to parse existing x config file '/etc/X11/xorg.conf'!". Still continues working nicely, but once I log out it reverts to a single screen so i have to start over with each new session.  Have tried running "gksu nvidia-settings" and "sudo nvidia-xconfig".  Neither makes a blind bit of difference, I still can't save the settings.  I'm still pretty new to linux so don't understand the code.  Any idiot-proof help will be hugely appreciated!  Cheers!  bob.

---

### Post by bangeko on 2009-04-26
I have same problem "Failed to parse existing X config file '/etc/X11/xorg.conf"

---

### Post by innominate227 on 2009-04-26
> **Jæd said:**
> Was this solved...? I had this and in the end I copied and pasted the file contents displayed when the "Preview" button was pressed.

This worked for me as well.  NOTE: in order to get to the preview button you need to rename your current xorg.conf (its in /etc/X11)

---

### Post by ajayrockrock on 2009-04-28
How I fixed it:

1)  open a terminal
2)  sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2)  sudo touch /etc/X11/xorg.conf  
3)  sudo nvidia-settings
4)  hit "save configuration"

with the empty xorg.conf, nvidia-settings should properly save the file.

---

### Post by bangeko on 2009-04-28
> **ajayrockrock said:**
> How I fixed it:

1)  open a terminal
2)  sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2)  sudo touch /etc/X11/xorg.conf  
3)  sudo nvidia-settings
4)  hit "save configuration"

with the empty xorg.conf, nvidia-settings should properly save the file.

Yes, it works

---

### Post by terrordrone on 2009-04-29
Guys im in need of help..  Sorry to post in this thread.. but im facing very similar issues

my office desk has kubuntu 8.10 .. 

suddenly the resolution is set to 800x600 .. there is no other higher options available..

output from xrandr :

```

Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0
   640x480        60.0
   400x300        60.0     56.0
   320x240        60.0

```

lspci output : 
```

01:00.0 VGA compatible controller: nVidia Corporation NV18GL [Quadro NVS 280 SD] (rev c1)

```

xorg.conf :
```
....
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

how do i get it to use resolution of 1024 x 768 or higher ?

---

### Post by terrordrone on 2009-04-29
this is what i get when i run nvidia-settings :

```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```

on running nvidia-xconfig :
```
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

sh: pkg-config: not found
sh: pkg-config: not found
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

i restarted the system.. but when it reboots.. i dont even get kdm.. 
luckily i had backed xorg.conf file and replaced it.. then im back to 800x600 mode

---

### Post by sorryd on 2009-04-29
> **norwoods said:**
> run sudo nvidia-xconfig to create a new Xorg.conf.

if there is a problem with this, rename Xorg.conf and run sudo nvidia-xconfig.

I had the same problem as the top poster and this fixed it.
Using 9.04 with an 8600GT and twinview.

---

### Post by terrordrone on 2009-04-29
ive posted the output of running that command in my last post.. 

if i do it using sudo.. and then restart system.. i do not even get the login screen.. 

so had to go kill kdm and restore the backup xorg.conf file..

---

### Post by scootre on 2009-05-02
@terrordrone

I've had the same problems as you've described.  I honestly cannot believe they released this version of Ubuntu given there's a hell of a lot of other problems that have crept in (compared to Hardy).  :(

Anyway, this is what I did to get it working - the first part is what I've been doing in the past to lock the resolution for my system in Hardy:

Install EnvyNG

Launch EnvyNG (Applications > System) and installed the driver it recommended (for my system it was v173)

Restart the system.

From here your res might well be OK.  But for me, I run a few computers over a KVM so when I start my Kubuntu box it will default to a low res if the system does not have monitor focus when it boots - ie cannot see what monitor is connected)  So, to lock the resolution, I also did this:

Install nvidia-settings

Opened a terminal and ran:
```
$ sudo nvidia-settings
```
(must be run as root so settings can be saved to xorg.conf)

In EnvyNG, click X Server Configuration

In the display tab, my monitor was correctly identified (22" Acer AL2216w)

In the resolution pull-down list, select the desired res.  For me it is 1680x1050 @ 60Hz.

Click 'Save to X Configuration File'

Theoretically, that is it... and this is what I have done previously in Hardy (Kubuntu 8.04 and 8.10).  However, in 9.04, I find that I get an error and the changes to xorg.conf do not get saved (as per the OP of this thread).  I did try creating a blank xorg.conf using sudo touch... but I still couldn;t save the file.

I looked at the output to my console (because I'd launched nvidia-settings from the terminal, as root) and it complained that it didn't like a setting in xorg.conf.  I can't recalled the error but it related to the use of "Disable".  Looking at my xorg.conf I see a section that says:

```
Section "Module"
           Load "glx"
           Disable "dri2"
EndSection
```

So I opened xorg.conf and removed that section (and each time I do something like this I make a backup copy of the file!

Next I re ran nvidia-settings.  This time when I clicked the Save to X Configuration File it saved to the file.  All apeared to go OK though I got various mesaages about the use of "CoreKeyboard" and others in the existing file.  After a while, except the output from the console froze.  I waited for a while, got sick of waiting after about 1 min, hit Ctrl-c and then nvidia-settings closed.

I then restarted the system and all has been well since.

That all said, I presume the problem with trying to write to xorg.conf might be because of sections in it that nvidia-settings doesn't like because ENvyNG had shortly beforehand auto-edited it.

I'd be interested in comments about this.

Here's my xorg.conf

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL2216W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1680x1050_60 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```


Fun and games with Kubuntu 9.04.

---

### Post by terrordrone on 2009-05-04
sorry for the late reply guys

when i booted the machine today morning.. (had installed the nvidia-glx-96 before i went home through synaptic )

i got a pop up saying 'you are using restricted drivers and is not supported' or something like that..

i clicked on use the 96 driver and restarted the system..

my resolution is now 640x480 Sad


here is my new xorg.conf

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Mon Nov  3 08:46:46 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 280 SD"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select @1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

a pic of the settings page
[http://picasaweb.google.com/llabhilash/ForumPosts#5331800610901974354](http://picasaweb.google.com/llabhilash/ForumPosts#5331800610901974354)

---

### Post by MountainX on 2009-05-11
> **ajayrockrock said:**
> How I fixed it:

1)  open a terminal
2)  sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2)  sudo touch /etc/X11/xorg.conf  
3)  sudo nvidia-settings
4)  hit "save configuration"

with the empty xorg.conf, nvidia-settings should properly save the file.

I have a fresh install of Jaunty. I did these exact steps (copied and pasted into terminal) except #4 where I used gksudo.

Result:
```
root@myubuntu:~# mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
root@myubuntu:~# touch /etc/X11/xorg.conf 
root@myubuntu:~# gksudo nvidia-settings

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
At least one Device section is required.
```

Can anyone suggest a solution? (I don't want to use EnvyNG, even though I used it before and I like it. I'm trying to keep this install as standard as possible.)

---

### Post by alexpw on 2009-05-11
I also received this error.

```

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
At least one Device section is required

```To fix it, I did the following:

```

root@myubuntu:~# mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
root@myubuntu:~# touch /etc/X11/xorg.conf 

```

I then copied ONLY the "Device" section from the backup to the new conf, since that is what it said was required.  Mine was as follows:

```

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

```

I then ran nvidia-settings and saved successfully.

---

### Post by MountainX on 2009-05-11
> **alexpw said:**
> I also received this error.

I then ran nvidia-settings and saved successfully.

Thanks. That worked for me too.

---

### Post by djamu on 2009-05-13
Best method is to get things working:

remove any old xorg.conf / xorg.conf.backup
```

sudo rm /etc/X11/xorg.conf
sudo rm /etc/X11/xorg.conf.backup

```

create new clean xorg.conf
```

sudo nvidia-xconfig

```

modify & Save to X Configuration File> uncheck merge 
```

sudo nvidia-settings

```

Obviously this requires you to install the nvidia drivers & reboot first.

---

### Post by Sirgin on 2009-05-13
> **rgravenor said:**
> Hello!  I have the same issue.  I am trying to run two monitors in twinview off a single nvidia card.  I can it up to work beautifully using NVidia X server settings, but when i try to save it, it tells me "Failed to parse existing x config file '/etc/X11/xorg.conf'!". Still continues working nicely, but once I log out it reverts to a single screen so i have to start over with each new session.  Have tried running "gksu nvidia-settings" and "sudo nvidia-xconfig".  Neither makes a blind bit of difference, I still can't save the settings.  I'm still pretty new to linux so don't understand the code.  Any idiot-proof help will be hugely appreciated!  Cheers!  bob.Exactly the same situation here. One nVidia card, Twinview works perfectly but I can't save it.

I did however copy-paste the command line codes someone posted and I *think* I was able to save...we'll see after a reboot I suppose. :)

---

### Post by Sirgin on 2009-05-14
Awesome! It worked. :D

---

### Post by RJARRRPCGP on 2009-07-08
> **xkaliburx said:**
> 

Failed to parse existing X config file '/etc/X11/xorg.conf'!

Behind in the terminal screen I see;
ALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".



I have the same crap. :(

---

### Post by RJARRRPCGP on 2009-07-08
> **alexpw said:**
> To fix it, I did the following:

```

root@myubuntu:~# mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
root@myubuntu:~# touch /etc/X11/xorg.conf 

```

I then copied ONLY the "Device" section from the backup to the new conf, since that is what it said was required.  Mine was as follows:

```

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

```

I then ran nvidia-settings and saved successfully.

This fixed it. Thank you.

---

### Post by Sirgin on 2009-07-23
> **djamu said:**
> Best method is to get things working:

remove any old xorg.conf / xorg.conf.backup
```

sudo rm /etc/X11/xorg.conf
sudo rm /etc/X11/xorg.conf.backup

```

create new clean xorg.conf
```

sudo nvidia-xconfig

```

modify & Save to X Configuration File> uncheck merge 
```

sudo nvidia-settings

```

Obviously this requires you to install the nvidia drivers & reboot first.

Fantastic man, this worked for me in 9.04 :)

I had this problem when I was using 8.10 too. Then I used ajayrockrock's method to fix the problem. I decided to install 9.04 today and found the same problem. For some reason, ajayrockrock's method didn't work anymore, but yours did.

Thanks!

---

### Post by kukathe on 2009-10-06
> **ajayrockrock said:**
> How I fixed it:

1)  open a terminal
2)  sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2)  sudo touch /etc/X11/xorg.conf  
3)  sudo nvidia-settings
4)  hit "save configuration"

with the empty xorg.conf, nvidia-settings should properly save the file.

not work for me :(
```
alex@Karmic:~$ sudo touch /etc/X11/xorg.conf
alex@Karmic:~$ sudo nvidia-settings 

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
At least one Device section is required.

Segmentation fault (core dumped)
```

---

### Post by rnodal on 2009-10-11
> **alexpw said:**
> I also received this error.

```

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
At least one Device section is required

```To fix it, I did the following:

```

root@myubuntu:~# mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
root@myubuntu:~# touch /etc/X11/xorg.conf 

```

I then copied ONLY the "Device" section from the backup to the new conf, since that is what it said was required.  Mine was as follows:

```

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

```

I then ran nvidia-settings and saved successfully.

That did it for me. Thank you!!

-r

---

### Post by theZoid on 2009-10-15
Karmic Beta, this works with the old 'failed to parse' error we love:



```
1) open a terminal
2) sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2) sudo touch /etc/X11/xorg.conf
3) sudo nvidia-settings
4) hit "save configuration"
```

then copied ONLY the "Device" section from the backup to the new conf, since that is what it said was required. Mine was as follows:

```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection
```

I then ran nvidia-settings and saved successfully.  This for Karmic, and my blog....

---

### Post by linden940 on 2009-10-19
i have tryed and tryed...none of this is working 4 me!

i have the 9.04 and nothing i do is working

---

### Post by RJARRRPCGP on 2009-10-23
> **theZoid said:**
> Karmic Beta, this works with the old 'failed to parse' error we love:



```
1) open a terminal
2) sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2) sudo touch /etc/X11/xorg.conf
3) sudo nvidia-settings
4) hit "save configuration"
```

then copied ONLY the "Device" section from the backup to the new conf, since that is what it said was required. Mine was as follows:

```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection
```

I then ran nvidia-settings and saved successfully.  This for Karmic, and my blog....

Confirmed, also applies to Karmic Koala.

---

### Post by choyak on 2009-10-24
> **RJARRRPCGP said:**
> Confirmed, also applies to Karmic Koala.

Wow this was successful I am using Twinview in Karmic and I SAVED the conf in nvidia-config.  I am so happy because every time I switched on the PC I had to enter in the nvidia repeatedly

---

### Post by OrangeVixen on 2009-10-24
That works for me too, but if you had settings in the existing xorg.conf they don't get put into the new xorg.conf. So afterwards I had to carefully edit and copy the stuff I wanted in xorg.conf.backup to xorg.conf in an editor.

---

### Post by drKreso on 2009-10-27
> **djamu said:**
> Best method is to get things working:

remove any old xorg.conf / xorg.conf.backup
```

sudo rm /etc/X11/xorg.conf
sudo rm /etc/X11/xorg.conf.backup

```

create new clean xorg.conf
```

sudo nvidia-xconfig

```

modify & Save to X Configuration File> uncheck merge 
```

sudo nvidia-settings

```

Obviously this requires you to install the nvidia drivers & reboot first.
This helped

---

### Post by markackerman8@gmail.com on 2009-11-01
If all that doesnt work, here is what I needed to do ....

If you are trying to save your xorg.conf file after changing settings in the nvidia-settings app you may need to first replace it with

sudo nvidia-xconfig

This will back it up and then recreate it.  Seems a fresh install of Karmic Koala 9.10 doesn’t create a valid xorg.conf or it can’t parse it.  Whatever the case, that’s the fix.

Then you can
sudo nvidia-settings

---

### Post by Reynbow on 2009-11-03
Was having this exact same problem, this worked for me

> **djamu said:**
> Best method is to get things working:

remove any old xorg.conf / xorg.conf.backup
```

sudo rm /etc/X11/xorg.conf
sudo rm /etc/X11/xorg.conf.backup

```create new clean xorg.conf
```

sudo nvidia-xconfig

```modify & Save to X Configuration File> uncheck merge 
```

sudo nvidia-settings

```Obviously this requires you to install the nvidia drivers & reboot first.

---

### Post by jdmop1 on 2009-11-03
> **Reynbow said:**
> Was having this exact same problem, this worked for me


I'm still getting the dang error message.  I got it with 9.04 and 9.10.  
In the terminal, I am getting more though.

> VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Configured Screen Device".


My card is a PCI GeForce FX 5200 with 256MB RAM.

---

### Post by pootan on 2009-11-03
[jdmop1]("http://ubuntuforums.org/member.php?u=945572") I installed on a computer last night with that exact card. This is what I did after getting the message below and the one you previously mentioned with the "null" error



```

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
At least one Device section is required

```Open a terminal from Accessories>Terminal

Paste the following into the Terminal:

```

sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo touch /etc/X11/xorg.conf 

```Hit Enter
Now paste:
```
gksudo gedit /etc/X11/xorg.conf 
```Hit Enter
Now paste the following into the file that opened:
```

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

```press save at the top of that window

Now paste ```
 sudo nvidia-settings
```Hit Enter and highlight X Server Display Configuration
Press Save to X Configuration File

This time you should have a preview button you can view and save at the bottom.

Thanks to all the people in this thread.

---

### Post by neilg4rqn on 2009-11-07
Failed to parse existing x config file '/etc/X11/xorg.conf

It seems that the same routines do not work for al. Here is my fix.

I tried run sudo nvidia-xconfig to create a new Xorg.conf. and rename Xorg.conf and run sudo nvidia-xconfig but it didn't work for me. The file xorg.conf always had the same contents. I have it working now but I had to 

1	Run the NVidia X server asettings routine and then go to 'Save to X Configuration file' 
	do not save but view the contents copy and paste into a text file and save to the Desktop.

2	In a terminal window change directory to the one where xorg.conf lies "cd /etc/X11/"

3	sudo gedit xorg.conf

4	delete contents

5	Copy and paste contents of previously saved text file into the empty xorg.conf

6	Save it and to prove it works restart your machine.

Well it worked for me, and it's lots more fun than windoze...

---

### Post by jb1664 on 2009-11-08
Hi,
I've experienced similar problems. I installed ubuntu 9.10 and then install the nvidia driver version 96. I'm running it on a dell inspiron 8200 with an nvidia GeForce4 440 Go.
On reboot I get the loading page then the screen turn itself off.

I plugged an external monitor and found out that:
   - my laptop screen was set as secondary AND disabled
   - the external monitor was set at a low resolution of 640x480 (even so it's supposed to be 1280x1024) and is the primary monitor
I could change the setting back to the the laptop monitor to default but I couldn't save the configuration but I ran into more difficulties:
   -Failed to parse existing X config file '/etc/X11/xorg.conf'
   -I then removed the file '/etc/X11/xorg.conf' but i still couldn't save

The fix took me awhile to find out but it's now working smoothly. As I could not save the setting directly into the appropriate folder, I saved them on the desktop then copied the file to the appropriate folder. Steps below:

1) change the setting using nvidia X server settings

2) click save X configuration file and save the file onto the desktop

3) open terminal and type: gksudo nautilus (when I want move files that way I do not use command line but open a window with gksudo nautilus so I simply drag files from one window to the other, maybe not the right way but a bit more user friendly), enter your password.

4) navigate to the folder 'system/etc/X11'

5) drag and drop the file 'xorg.conf' and 'xorg.conf.backup' which were newly created, into the X11 folder

6) a file named "xorg.cong" already exist so you replace it, same with the other one.

7) restart your PC, and the settings should be saved.

I'm new to ubuntu so it might not be the best way but it's simple enough and worked for me :p
Let me know if that works for you.
JB

---

### Post by gslo on 2009-11-10
> **alexpw said:**
> I also received this error.

```

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
At least one Device section is required

```To fix it, I did the following:

```

root@myubuntu:~# mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
root@myubuntu:~# touch /etc/X11/xorg.conf 

```

I then copied ONLY the "Device" section from the backup to the new conf, since that is what it said was required.  Mine was as follows:

```

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

```

I then ran nvidia-settings and saved successfully.
Thank's works for me too!

---

### Post by vampalan on 2009-11-12
> **ajayrockrock said:**
> How I fixed it:

1)  open a terminal
2)  sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2)  sudo touch /etc/X11/xorg.conf  
3)  sudo nvidia-settings
4)  hit "save configuration"

with the empty xorg.conf, nvidia-settings should properly save the file.


This works except, it make makes my terminal app totally white. 
Does anyone else know how to fix this?

Edit: Fixed, follow this link. [http://ubuntuforums.org/showpost.php?p=7193930&postcount=6](http://ubuntuforums.org/showpost.php?p=7193930&postcount=6)

---

### Post by prkos on 2009-11-12
> **norwoods said:**
> run sudo nvidia-xconfig to create a new Xorg.conf.

if there is a problem with this, rename Xorg.conf and run sudo nvidia-xconfig.

Thank you, this solved it for me :)

All I did was
sudo nvidia-xconfig

I got this in terminal:
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


Then just 
gksudo nvidia-settings
and I was able to save the settings without errors.

---

### Post by vampalan on 2009-11-13
> **vampalan said:**
> This works except, it make makes my terminal app totally white. 
Does anyone else know how to fix this?

Edit: Fixed, follow this link. [http://ubuntuforums.org/showpost.php?p=7193930&postcount=6](http://ubuntuforums.org/showpost.php?p=7193930&postcount=6)

I noticed the above link that I quote turns off the effects, and turning them back on causes the same blank screen problems. Anyone with any clues?

---

### Post by angelsguitar on 2009-11-14
> **djamu said:**
> Best method is to get things working:

remove any old xorg.conf / xorg.conf.backup
```

sudo rm /etc/X11/xorg.conf
sudo rm /etc/X11/xorg.conf.backup

```

create new clean xorg.conf
```

sudo nvidia-xconfig

```

modify & Save to X Configuration File> uncheck merge 
```

sudo nvidia-settings

```

Obviously this requires you to install the nvidia drivers & reboot first.

Worked wonderfully in Karmic. Thanks.

---

### Post by djamu on 2009-11-14
mm I'm getting popular here ( just kidding :D )

mmm did anyone figure out how to get multiGPU cards working ?
I don't seem to be able to use more then 1 GPU core for multiple outs...
( don't need / want SLI ) :rolleyes:

---

### Post by RazorV on 2009-11-17
> **pootan said:**
> [jdmop1]("http://ubuntuforums.org/member.php?u=945572") I installed on a computer last night with that exact card. This is what I did after getting the message below and the one you previously mentioned with the "null" error



```

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
At least one Device section is required

```Open a terminal from Accessories>Terminal

Paste the following into the Terminal:

```

sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo touch /etc/X11/xorg.conf 

```Hit Enter
Now paste:
```
gksudo gedit /etc/X11/xorg.conf 
```Hit Enter
Now paste the following into the file that opened:
```

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

```press save at the top of that window

Now paste ```
 sudo nvidia-settings
```Hit Enter and highlight X Server Display Configuration
Press Save to X Configuration File

This time you should have a preview button you can view and save at the bottom.

Thanks to all the people in this thread.


This is the only way it worked for me!  Thanks so much!

---

### Post by shellnet on 2009-11-20
The steps:
1) open a terminal
2) sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2) sudo touch /etc/X11/xorg.conf
3) sudo nvidia-settings
4) hit "save configuration

DID NOT work for me still got the "Failed to parse existing x config file '/etc/X11/xorg.conf'!"

This DID work:
1) sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2) sudo nvidia-settings
3) click nvidia-settings Configuration
4) click Save Current Configuration
5) click preview
6) copy output
7) sudo nano /etc/X11/xorg.conf
8) paste preview output and write out

---

### Post by djamu on 2009-11-20
> **shellnet said:**
> The steps:
1) open a terminal
2) sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2) sudo touch /etc/X11/xorg.conf
3) sudo nvidia-settings
4) hit "save configuration

DID NOT work for me still got the "Failed to parse existing x config file '/etc/X11/xorg.conf'!"



it's obvious that this won't ever work.. file is empty and lacking correct permissions.

doing a 
```
sudo nano /etc/X11/xorg.conf
```
gives it the right permissions.... but if you want even more complicated ways to do the same ... I know a couple ( including a re-install ):lolflag: 
It's obvious that you have no idea how permissions work.


**The recommended method by nvidia** is the one I described
and works for 99% of the users 
first delete all old *.conf files
then
```
nvidia-xconfig
```
then
```
sudo nvidia-settings
```

if that doesn't work > check that nvidia-xconfig has actually written something in the config file ( in rare cases the parent directory is lacking the right permissions ).
to fix this.
```
sudo chmod 777 /etc/X11
```
and run 
```
nvidia-xconfig
```
again

if still there's nothing in the file.

do 
```
sudo gedit /etc/X11/xorg.conf
```

and put this in it
```

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

```
now run 
```
sudo nvidia-settings
```
again.

and all is good.

---

### Post by shellnet on 2009-11-20
[QUOTE=djamu;8357036]it's obvious that this won't ever work.. file is empty and lacking correct permissions.

doing a 
```
sudo nano /etc/X11/xorg.conf
```
gives it the right permissions.... but if you want even more complicated ways to do the same ... I know a couple ( including a re-install ):lolflag: 
It's obvious that you have no idea how permissions work.

......

Wow. I do have SOME idea how permissions work and I appreciate your helpful and very constructive message.

---

### Post by pelgrim on 2009-11-21
I have a similar problem with nvidia as described in next thread:

[http://ubuntuforums.org/showthread.php?t=1332413&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=1332413&highlight=nvidia)

first I had the problem like you all had here,
but I found how to use nvidia-xconfig and nvidia-settings

problem here is that X will not start again once nvidia-xconfig
has written an xorg.conf file.
The only way I get my system running again is log on in console
and delete xorg.conf.
Which leaves me without my nvidia driver ...

---

### Post by denouement on 2009-11-23
I was having this issue as well, along with some complications like what has been described.

This worked for me:

> **norwoods said:**
> sudo nvidia-xconfig 


nvidia-xconfig automatically replaced the bad .conf file with a good one and I was able to save.

Hope that helps.

---

### Post by phuqwit on 2009-11-26
Had the same issue and none of the above worked.  Added the line: Device          "Default Device" in the screen section and it was able to parse correctly

---

### Post by coolnezz on 2009-11-27
Thank you, this worked for me.
I can't believe Ubuntu is still as buggy as crap!
Even a simple file sharing still gives some error!
It still aint ready for primetime like M$!
pissing me off right now, it's 4:30AM!
----------------------------------------------------------------

> **alexpw said:**
> I also received this error.

```

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
At least one Device section is required

```To fix it, I did the following:

```

root@myubuntu:~# mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
root@myubuntu:~# touch /etc/X11/xorg.conf 

```

I then copied ONLY the "Device" section from the backup to the new conf, since that is what it said was required.  Mine was as follows:

```

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

```

I then ran nvidia-settings and saved successfully.

---

### Post by docdross on 2009-11-28
OK, I admit I am a rank nube to linux and there is a world of info I need to learn (that's why I am here).
I am running Ubuntu 9.10 64 BIT (just installed and fully patched). I install the recomended Nvidia driver (v173). I get "Failed to parse existing X config file '/etc/X11/xorg.conf'!" EVERY TIME! I have followed several dozen procedures from this forum and others...NOTHING WORKS - HEEEELP!
jt

---

### Post by tojam on 2009-11-29
> **phuqwit said:**
> Had the same issue and none of the above worked.  Added the line: Device          "Default Device" in the screen section and it was able to parse correctly
Yep this seems to be the root of the problem.

The screen section of the  config file doesn't specify a device, this is exactly what the error says, when you read it.

   > "Undefined Device "(null)" referenced by Screen "Default Screen".

Modify the "Screen" section to specify a Device, in my case this is "Default Device" and you're in business

Section "Screen"
     ...
    **Device         "Default Device"**
     ...
EndSection

Section "Device"
    Identifier     "Default Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

---

### Post by docdross on 2009-11-29
OK then.

This is the contents of my xorg.config now.


Section "Screen"
    Device "Default Device"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Now I get the message: Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

Am I making progress???

---

### Post by rjaguar3 on 2009-11-30
What worked for me was to click on Save to X Configuration File, then Show Preview.  Copying the text that appears in the preview window and sudo gedit-ing xorg.conf and pasting the text there to overwrite the old file does the job after restarting the X server (if necessary).

---

### Post by superotakuman on 2009-11-30
This worked perfect for the 64-bit version, but not the 32-bit version. Have any clue why that is? I have a 128meg video card, using driver version 173. Please help.

---

### Post by krozzie on 2009-12-08
@alexpw post #18

Worked for me !!! , using 9.10 32bit. Using a 01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
Also should add, using the 185 driver

---

### Post by roddo1966 on 2009-12-08
Yep, same thing worked for me.
I removed the 'screen' section (first section) of the xorg.conf file, then ran 'sudo nvidia-settings' in the terminal. It only then gave me the option of merging the generated file with the existing file.
Using an empty xorg.conf just produced an error.
Thanks, all!

---

### Post by Kenrro on 2009-12-10
Thanks, removing the xorg.conf  and using nvidia-xconfig solved the problem.

This in ubuntu karmic.

---

### Post by dr.sehs on 2009-12-12
> **pootan said:**
> [jdmop1]("http://ubuntuforums.org/member.php?u=945572") I installed on a computer last night with that exact card. This is what I did after getting the message below and the one you previously mentioned with the "null" error



```

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
At least one Device section is required

```Open a terminal from Accessories>Terminal

Paste the following into the Terminal:

```

sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo touch /etc/X11/xorg.conf 

```Hit Enter
Now paste:
```
gksudo gedit /etc/X11/xorg.conf 
```Hit Enter
Now paste the following into the file that opened:
```

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

```press save at the top of that window

Now paste ```
 sudo nvidia-settings
```Hit Enter and highlight X Server Display Configuration
Press Save to X Configuration File

This time you should have a preview button you can view and save at the bottom.

Thanks to all the people in this thread.


thank you [jdmop1]("http://ubuntuforums.org/member.php?u=945572") this is the only solution that work with me ...

and thank you for all user who try to help in this thread :D

---

### Post by webbdawg on 2009-12-12
I just got over my [monitor issues]("http://ubuntuforums.org/showthread.php?t=1339720") with the suggestion from Howefield, worked like a charm.

> gksudo nvidia-settings

it opens the applet as root and writes to the config file.. I guess Nvidia does not know how to ask for the root password so we have to open it as such.

---

### Post by hendo on 2009-12-17
> **pootan said:**
> [jdmop1]("http://ubuntuforums.org/member.php?u=945572") I installed on a computer last night with that exact card. This is what I did after getting the message below and the one you previously mentioned with the "null" error



```

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
At least one Device section is required

```Open a terminal from Accessories>Terminal

Paste the following into the Terminal:

```

sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo touch /etc/X11/xorg.conf 

```Hit Enter
Now paste:
```
gksudo gedit /etc/X11/xorg.conf 
```Hit Enter
Now paste the following into the file that opened:
```

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

```press save at the top of that window

Now paste ```
 sudo nvidia-settings
```Hit Enter and highlight X Server Display Configuration
Press Save to X Configuration File

This time you should have a preview button you can view and save at the bottom.

Thanks to all the people in this thread.Thankyou very much. This guide worked for me.

Ubuntu 9.10
nVidia Geforce FX5200

---

### Post by mmmmf on 2009-12-26
I had the same problem, I got it fixed though thankfully for you guys. But now every time I load any application, the windows always load to the left side of my monitor, it doesn't remember the window positions, just the size. Any help?

(edit)

My settings on compiz for some reason changed, I switched them back though.

---

### Post by aaronchall on 2009-12-29
Quite right, as I discovered, that list doesn't work, at least not as I discovered on my Inspiron 9300...

> **djamu said:**
> it's obvious that this won't ever work.. 
...

**The recommended method by nvidia** is the one I described
and works for 99% of the users 
first delete all old *.conf files
then
```
nvidia-xconfig
```then
```
sudo nvidia-settings
```if that doesn't work > check that nvidia-xconfig has actually written something in the config file ( in rare cases the parent directory is lacking the right permissions ).
to fix this.
```
sudo chmod 777 /etc/X11
```and run 
```
nvidia-xconfig
```again

if still there's nothing in the file.

do 
```
sudo gedit /etc/X11/xorg.conf
```and put this in it
```

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

```now run 
```
sudo nvidia-settings
```again.

and all is good.

This worked for me, but only after I THEN restarted my X server by:
```
sudo /etc/init.d/gdm restart
```Ctrl-Alt-Backspace doesn't work for me for some reason...

---

### Post by cybrid on 2009-12-29
This is "funny" I was having the same problem you all have had on an old machine of mine (Pentium IV + 6800XT) and after applying your solution I got a "working" xorg.conf, and I say working between quotes because every time I restart I still get 1024x768 instead of the 1680x1050 configured in the conf file, any ideas on this?

This is my current xorg.conf :

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Fri Aug 14 17:54:58 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Unknown"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1680x1050_60 +0+0; nvidia-auto-select +0+0; 1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

P.S: Please, If somebody could help me; this is really urgent

Edit:

Ok, it's almost 7 am now but I managed to fix it. It happened that on top of the problem described here, after getting a working xorg.conf, the gnome x settings had kept the old resolution and they were overwriting the nvidia settings. I just had to change the resolution in the gnome settings for it to work.

Also, I think this should be a how-to. In my search over the net on how to solve this issue I've found out that there seems to be quite a few people suffering from this.

---

### Post by rocketero on 2009-12-30
> **jb1664 said:**
> Hi,
I've experienced similar problems. I installed ubuntu 9.10 and then install the nvidia driver version 96. I'm running it on a dell inspiron 8200 with an nvidia GeForce4 440 Go.
On reboot I get the loading page then the screen turn itself off.

I plugged an external monitor and found out that:
   - my laptop screen was set as secondary AND disabled
   - the external monitor was set at a low resolution of 640x480 (even so it's supposed to be 1280x1024) and is the primary monitor
I could change the setting back to the the laptop monitor to default but I couldn't save the configuration but I ran into more difficulties:
   -Failed to parse existing X config file '/etc/X11/xorg.conf'
   -I then removed the file '/etc/X11/xorg.conf' but i still couldn't save

The fix took me awhile to find out but it's now working smoothly. As I could not save the setting directly into the appropriate folder, I saved them on the desktop then copied the file to the appropriate folder. Steps below:

1) change the setting using nvidia X server settings

2) click save X configuration file and save the file onto the desktop

3) open terminal and type: gksudo nautilus (when I want move files that way I do not use command line but open a window with gksudo nautilus so I simply drag files from one window to the other, maybe not the right way but a bit more user friendly), enter your password.

4) navigate to the folder 'system/etc/X11'

5) drag and drop the file 'xorg.conf' and 'xorg.conf.backup' which were newly created, into the X11 folder

6) a file named "xorg.cong" already exist so you replace it, same with the other one.

7) restart your PC, and the settings should be saved.

I'm new to ubuntu so it might not be the best way but it's simple enough and worked for me :p
Let me know if that works for you.
JB

thank yoy for posting this solution, it was the only one it fixed my dual monitors problem. [http://ubuntuforums.org/images/icons/icon7.gif](http://ubuntuforums.org/images/icons/icon7.gif)

---

### Post by djamu on 2009-12-31
> **aaronchall said:**
> 
.....
This worked for me, but only after I THEN restarted my X server by:
```
sudo /etc/init.d/gdm restart
```Ctrl-Alt-Backspace doesn't work for me for some reason...

yes of course, I forgot to mention that, 
The Ubuntu devs disabled the "Ctrl-Alt-Backspace" GDM reset in 9.04 and 9.10
( don't ask me why, I guess it's too handy as they might prefer a gui with lots of buttons > hello vista :lolflag: )

---

### Post by djamu on 2009-12-31
> **cybrid said:**
> 
......
This is "funny" I was having the same problem you all have had on an old machine of mine (Pentium IV + 6800XT) and after applying your solution I got a "working" xorg.conf, and I say working between quotes because every time I restart I still get 1024x768 instead of the 1680x1050 configured in the conf file, any ideas on this?

.......
Ok, it's almost 7 am now but I managed to fix it. It happened that on top of the problem described here, after getting a working xorg.conf, the gnome x settings had kept the old resolution and they were overwriting the nvidia settings. I just had to change the resolution in the gnome settings for it to work.
.........


Dear Cybrid

The problem you described is caused by wrong buffered UPNP capability info provided by your screen ( not a flatscreen but a CRT one right ? )..
and I'm also pretty sure the screen has 2 connectors for dual usage ( 2 computers / 1 screen ) or a KVM switch ...
( I've had that problem a couple of years back when I was using Sony CRT's ) 

The solution is quite simple ( but still annoying ) > just unplug / plug the power cord of your monitor for a couple of seconds just before boot / between reboot / after switching your screen from one computer to the other. 
This will reset the UPNP info provided by your screen

( This is not a debian/ubuntu/gnome bug, but actually a bug in the firmware  of your screen / a different polling method from the OS might also do the trick, but since these CRT's are phased out there's not really a point in fixing this )

Happy NY to y'all

:popcorn:

---

### Post by greggc2006 on 2009-12-31
Did'nt work for me!! I'm stuck at 640x480 on my projector screen and nothing on my LCD. My xorg.conf now reads:-

[HTML]# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Fri Aug 14 18:33:37 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    FontPath        "unix/:7100"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

[/HTML]

Any help is great, really simple help is perfect!!

---

### Post by cybrid on 2009-12-31
> **djamu said:**
> Dear Cybrid

The problem you described is caused by wrong buffered UPNP capability info provided by your screen ( not a flatscreen but a CRT one right ? )..
and I'm also pretty sure the screen has 2 connectors for dual usage ( 2 computers / 1 screen ) or a KVM switch ...
( I've had that problem a couple of years back when I was using Sony CRT's ) 

The solution is quite simple ( but still annoying ) > just unplug / plug the power cord of your monitor for a couple of seconds just before boot / between reboot / after switching your screen from one computer to the other. 
This will reset the UPNP info provided by your screen

( This is not a debian/ubuntu/gnome bug, but actually a bug in the firmware  of your screen / a different polling method from the OS might also do the trick, but since these CRT's are phased out there's not really a point in fixing this )

Happy NY to y'all

:popcorn:

Err, nope, my monitor is a 20'' Samsung TFT, more accurately a Samsung SyncMaster 2032BW, but you might have a point since that was the monitor I changed to after trying another tft, an older 17'' LG, which only had VGA input and not DVI.

---

### Post by redcap on 2010-01-07
> **djamu said:**
> Best method is to get things working:

remove any old xorg.conf / xorg.conf.backup
```

sudo rm /etc/X11/xorg.conf
sudo rm /etc/X11/xorg.conf.backup

```create new clean xorg.conf
```

sudo nvidia-xconfig

```modify & Save to X Configuration File> uncheck merge 
```

sudo nvidia-settings

```Obviously this requires you to install the nvidia drivers & reboot first.

I was having problems not saving, and this was the solution for me. Thanks djamu!

---

### Post by WarmonkeyUK on 2010-01-12
Not sure if this has been mentioned in the thread already, but I solved this issue by manually selecting the resolution and refresh rate settings in the Nvidia X Server Settings utility. Leaving them at their default settings of 'Auto' didn't seem to work, as something was missing from the xorg.conf file. By manually selecting them, I think you forcibly write them into the configuration file. If someone else could confirm this fix, or tell me I'm talking a load of rubbish, I'd greatly appreciate it.

---

### Post by master620 on 2010-01-12
> **djamu said:**
> Best method is to get things working:

remove any old xorg.conf / xorg.conf.backup
```

sudo rm /etc/X11/xorg.conf
sudo rm /etc/X11/xorg.conf.backup

```create new clean xorg.conf
```

sudo nvidia-xconfig

```modify & Save to X Configuration File> uncheck merge 
```

sudo nvidia-settings

```Obviously this requires you to install the nvidia drivers & reboot first.

THANK YOU SO MUCH! Although this was done back in may in 2009, this worked FLAWLESSLY. just copy and paste everything he did, and it will work without a problem!

---

### Post by fishkid257936 on 2010-01-16
Hi i am new. I got it to save the info, but the windows to not have a title bar. The terminal is completely white. Is there a way to fix this?? :(

---

### Post by djamu on 2010-01-16
Sigh....

Are you clairvoyant ?, neither am I, or anyone else on this forum.

The more info you provide, the more likely people will give you a decent answer, 
for example, how about 

> what hardware card do you have ( nvidia / ati )
> how many monitors ?
> installed driver version
> additional packages you installed.


But since this is your first post, here goes..

**answer:**

[B]most likely your window decorator isn't running.
[/B]

**click** > System > Preferences > Appearance, Visual Effects tab?

are there additional settings, can you enable them there ?

I could give you a couple of links with answers, but what to do depends on the info you have to give. 
And please do yourself a favor > avoid old posts ( pre 2009 ).. these are completely outdated and should be ignored ( that includes all "xorg.conf" howto's


awaiting your reply


Also:
you know, there's a search function on this forum :rolleyes:
( search for "white terminal" )
a google on "ubuntu white terminal gives > 489,000 results, about any of those on the first page will give you some answers ( do check the date of posts > skip older posts...


but whatever, I might as well help you here and redirect you later ( question is also off-topic )#-o

---

### Post by fishkid257936 on 2010-01-17
NVIDIA Card Version 96.43.13
1 monitor
started after reboot changing xorg.conf file.
Figured out how to workaround problem but no visual effects. Turned it to Normal to none. But would be great to be able to use visual effects.

---

### Post by djamu on 2010-01-18
> **fishkid257936 said:**
> NVIDIA Card Version 96.43.13

1 monitor

started after reboot changing xorg.conf file.

Figured out how to workaround problem but no visual effects. Turned it to Normal to none. But would be great to be able to use visual effects.

driver version 96.43.13 ? why such on old one ? that one is ancient. ( might well be the reason )
what graphical card do you have btw ?
ubuntu version ? 32 / 64 bit ? 
did you manually edit xorg.conf ? > **don't** 

either install the latest driver from the repository ( 185 I believe ), or download the latest from nvidia ( 190.52 ) and compile it. ( very easy )
**Compiling the latest nvidia driver:**
note following onto a piece of paper

> download driver from nvidia to /tmp  ( make sure it matches your architecture (32/64 bit) )

in a terminal type.
```
sudo /etc/init.d/gdm stop  
```

this will kill your current gnome session ( save all open files before doing that )

login and then type
```
cd /tmp
sudo chmod +x NVIDIA-Linux-x86_64-190.53-pkg2
```  

this will make the installer executable 

TIP: you don't (ever) have to type the complete name > just type sudo chmod +x NV  and press 2x the TAB key ( it will autocomplete, this works with any command )

then do 
```
sudo ./NVIDIA-Linux-x86_64-190.53-pkg2
``` and press enter 

this will start compiling the latest driver > answer yes to all questions.

after that 
```
sudo /etc/init.d/gdm start 
```

this will start gnome again ( with the new driver )

adjust your screen to your liking
```
sudo nvidia-settings
``` and save it.

if the white terminal still exists > come back.



if it works, my **essential eyecandy:**
> click > System > Prefences > Appearance > Visual Effects > extra ...

close 
open synaptic ( enable all repositories and reload ) 

**install:**
fusion-icon,emerald,compizconfig-settings-manager,avant-window-navigator,desklets,screenlets

**fusion-icon** > compiz management 

--switch between compiz/metacity window managers 
--switch between gtk/emarald windows decorators
--access compiz settings manager ( here's where all the goodies are )
--access emerald theme manager > install cool decorators ( install decorator themes before enbling them !!! )

> 25 cool themes > [http://www.webupd8.org/2009/06/25-great-looking-compiz-emerald-themes.html]("http://www.webupd8.org/2009/06/25-great-looking-compiz-emerald-themes.html")
> theme repository > [URL="http://compiz-themes.org/index.php?xcontentmode=103"]http://compiz-themes.org/index.php?xcontentmode=103 
[/URL]
 
**important: enabling "loose bindings" in compiz options will improve performance on Nvidia cards **



**avant-window-navigator** OSX style panel

**desklets,screenlets** gnome widgets


**blurred transparancy howto** ( look at my screenshot )

Enabling transparancy blur in compiz alone won't work 2 steps : 
> Open emerald theme manager > Emerald settings > Compiz Decoration Blur Type > All decoration
> Open Compiz settings manager > Blur Windows > pick either Gaussian / Mipmap ( what works best for you ) 

high res screenshot > [http://3d.uk.to/files/desktop/screenshot.jpg]("http://3d.uk.to/files/desktop/screenshot.jpg")

:popcorn:

---

### Post by fishkid257936 on 2010-01-18
um.. ok, after I kill, I see a blank screen. I searched online and people were saying remove a line from /boot/grub/menu.lst. My system does not even have this file. I want to be able to install the latest driver!

---

### Post by fishkid257936 on 2010-01-18
Oh never mind. Just had to install some updates.

---

### Post by fishkid257936 on 2010-01-18
when ran, it said it was not supported.
Here is log:
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Jan 18 08:35:15 2010
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
WARNING: The NVIDIA GeForce2 MX/MX 400 GPU installed in this system is
         supported through the NVIDIA 96.43.xx legacy Linux graphics drivers. 
         Please visit http://www.nvidia.com/object/unix.html for more
         information.  The 190.53 NVIDIA Linux graphics driver will ignore this
         GPU.
WARNING: You do not appear to have an NVIDIA GPU supported by the 190.53 NVIDIA
         Linux graphics driver installed in this system.  For further details,
         please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README
         available on the Linux driver download page at www.nvidia.com.
-> License accepted.
-> Installing NVIDIA driver version 190.53.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.31-17-generic/build'
-> Kernel output path: '/lib/modules/2.6.31-17-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.31-17-gener
   ic/build SYSOUT=/lib/modules/2.6.31-17-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.31-17-generic/build SUBDIRS
   =/tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
       echo;                                \
       echo "  ERROR: Kernel configuration is invalid.";        \
       echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";    \
       echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";    \
       echo;                                \
       /bin/false)
   mkdir -p /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/.tmp_versio
   ns ; rm -f /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/.tmp_vers
   ions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz2004/NVIDIA-Linux-x86-190.53-p
   kg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/.nv.o.d
    -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iinclude  -I
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include -include include/l
   inux/autoconf.h -Iubuntu/include  -D__
   KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasi
   ng -fno-common -Werror-implicit-function-declaration -Wno-format-security -f
   no-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct
   -return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=g
   eneric32 -ffreestanding -fstack-protector -fstack-protector-all -pipe -Wno-s
   ign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno
   -3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-siblin
   g-calls -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow
   -fno-dwarf2-cfi-asm -I/tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparen
   theses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-comp
   are -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRI
   NG=\"190.53\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KB
   UILD_BASENAME=KBUILD_STR(nv)"  -D"K
   BUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2004/NVIDIA-Linux-x86-19
   0.53-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/
   usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv.c:14:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜set_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type â€˜void *â€™ used in arithmetic
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜clear_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type â€˜void *â€™ used in arithmetic
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜change_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type â€˜void *â€™ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/prefetch.h: In function â€˜prefetch_rangeâ€™:
   include/linux/prefetch.h:57: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/sched.h: In function â€˜object_is_on_stackâ€™:
   include/linux/sched.h:2185: warning: pointer of type â€˜void *â€™ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv.c:14:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/io.h: In funct
   ion â€˜writeqâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type â€˜void *â€™ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/scatterlist.h: In function â€˜sg_virtâ€™:
   include/linux/scatterlist.h:199: warning: pointer of type â€˜void *â€™ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv.c:14:
   include/asm-generic/dma-mapping-common.h: In function â€˜dma_map_pageâ€™:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type â€˜voi
   d *â€™ used in arithmetic
   In file included from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:119,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/highmem.h: In function â€˜zero_user_segmentsâ€™:
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/nv.c: In function â€
   ˜nv_kern_openâ€™:
   /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/nv.c:2188: warning: 
   initialization from incompatible pointer type
     cc -Wp,-MD,/tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/.nv_gvi
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iinclud
   e  -I/usr/src/linux-headers-2.6.31-17-generic/arch/x86/include -include incl
   ude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-p
   rototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-f
   unction-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2
   -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary
   =2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack-pr
   otector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwi
   nd-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -f
   no-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statem
   ent -Wno-pointer-sign -fno-st
   rict-overflow -fno-dwarf2-cfi-asm -I/tmp/selfgz2004/NVIDIA-Linux-x86-190.53-
   pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subs
   cripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -
   MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DN
   V_VERSION_STRING=\"190.53\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_ST
   R(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_gvi)"  -D"KBUILD_MODNAME=KBUILD_ST
   R(nvidia)"  -c -o /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/.t
   mp_nv_gvi.o /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/nv_gvi.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv_gvi.c:15:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜set_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type â€˜void *â€™ used in arithmetic
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜clear_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type â€˜void *â€™ used in arithmetic
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜change_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type â€˜void *â€™ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv_gvi.c:15:
   include/linux/prefetch.h: In function â€˜prefetch_rangeâ€™:
   include/linux/prefetch.h:57: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv_gvi.c:15:
   include/linux/sched.h: In function â€˜object_is_on_stackâ€™:
   include/linux/sched.h:2185: warning: pointer of type â€˜void *â€™ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv_gvi.c:15:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/io.h: In funct
   ion â€˜writeqâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type â€˜void *â€™ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv_gvi.c:15:
   include/linux/scatterlist.h: In function â€˜sg_virtâ€™:
   include/linux/scatterlist.h:199: warning: pointer of type â€˜void *â€™ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv_gvi.c:15:
   include/asm-generic/dma-mapping-common.h: In function â€˜dma_map_pageâ€™:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type â€˜voi
   d *â€™ used in arithmetic
   In file included from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:119,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv_gvi.c:15:
   include/linux/highmem.h: In function â€˜zero_user_segmentsâ€™:
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/.nv-vm.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iinclude
    -I/usr/src/linux-headers-2.6.31-17-generic/arch/x86/include -include includ
   e/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -
   m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=
   2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack-pro
   tect
   or -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-ta
   bles -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-om
   it-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -
   Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/tmp/selfgz2004/
   NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswi
   tch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar 
   -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERN
   EL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"190.53\" -UDEBUG -U_DEBUG -DNDEBU
   G  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"K
   BUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2004/NVIDIA-Linux-x86-19
   0.53-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pk
   g1/usr/src/nv/nv-vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-vm.c:14:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜set_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type â€˜void *â€™ used in arithmetic
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜clear_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type â€˜void *â€™ used in arithmetic
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜change_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type â€˜void *â€™ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/linux/prefetch.h: In function â€˜prefetch_rangeâ€™:
   include/linux/prefetch.h:57: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/linux/sched.h: In function â€˜object_is_on_stackâ€™:
   include/linux/sched.h:2185: warning: pointer of type â€˜void *â€™ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-vm.c:14:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/io.h: In funct
   ion â€˜writeqâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type â€˜void *â€™ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/linux/scatterlist.h: In function â€˜sg_virtâ€™:
   include/linux/scatterlist.h:199: warning: pointer of type â€˜void *â€™ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/asm-generic/dma-mapping-common.h: In function â€˜dma_map_pageâ€™:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type â€˜voi
   d *â€™ used in arithmetic
   In file included from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:119,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/linux/highmem.h: In function â€˜zero_user_segmentsâ€™:
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/.os-agp
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iinclud
   e  -I/usr/src/linux-headers-2.6.31-17-generic/arch/x86/include -include incl
   ude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-p
   rototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-i
   mplicit-function-declaration -Wno-format-security -fno-delete-null-pointer-c
   hecks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stac
   k-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding 
   -fstack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchr
   onous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-th
   an=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-af
   ter-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/
   tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv -Wall -Wimplicit -Wre
   turn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith 
   -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno
   -error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"190.53\" -UDEBUG -
   U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_ST
   R(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2004/NVI
   DIA-Linux-x86-190.53-pkg1/usr/src/nv
   /.tmp_os-agp.o /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/os-ag
   p.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-agp.c:24:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜set_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type â€˜void *â€™ used in arithmetic
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜clear_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type â€˜void *â€™ used in arithmetic
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜change_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type â€˜void *â€™ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-agp.c:24:
   include/linux/prefetch.h: In function â€˜prefetch_rangeâ€™:
   include/linux/prefetch.h:57: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-agp.c:24:
   include/linux/sched.h: In function â€˜object_is_on_stackâ€™:
   include/linux/sched.h:2185: warning: pointer of type â€˜void *â€™ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-agp.c:24:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/io.h: In funct
   ion â€˜writeqâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type â€˜void *â€™ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-agp.c:24:
   include/linux/scatterlist.h: In function â€˜sg_virtâ€™:
   include/linux/scatterlist.h:199: warning: pointer of type â€˜void *â€™ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-agp.c:24:
   include/asm-generic/dma-mapping-common.h: In function â€˜dma_map_pageâ€™:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type â€˜voi
   d *â€™ used in arithmetic
   In file included from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:119,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-agp.c:24:
   include/linux/highmem.h: In function â€˜zero_user_segmentsâ€™:
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/.os-int
   erface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -I
   include  -I/usr/src/linux-headers-2.6.31-17-generic/arch/x86/include -includ
   e include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wst
   rict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-impl
   icit-function-declaration -Wno-format-security -fno-delete-null-pointer-chec
   ks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-b
   oundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fs
   tack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchrono
   us-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=
   1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after
   -statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/tmp
   /selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv -Wall -Wimplicit -Wretur
   n-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wn
   o-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-er
   ro
   r -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"190.53\" -UDEBUG -U_DEB
   UG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_
   interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2004/NV
   IDIA-Linux-x86-190.53-pkg1/usr/src/nv/.tmp_os-interface.o /tmp/selfgz2004/NV
   IDIA-Linux-x86-190.53-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-interface.c:26:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜set_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type â€˜void *â€™ used in arithmetic
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜clear_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type â€˜void *â€™ used in arithmetic
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜change_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type â€˜void *â€™ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-interface.c:26:
   include/linux/prefetch.h: In function â€˜prefetch_rangeâ€™:
   include/linux/prefetch.h:57: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-interface.c:26:
   include/linux/sched.h: In function â€˜object_is_on_stackâ€™:
   include/linux/sched.h:2185: warning: pointer of type â€˜void *â€™ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-interface.c:26:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/io.h: In funct
   ion â€˜writeqâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type â€˜void *â€™ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-interface.c:26:
   include/linux/scatterlist.h: In function â€˜sg_virtâ€™:
   include/linux/scatterlist.h:199: warning: pointer of type â€˜void *â€™ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-interface.c:26:
   include/asm-generic/dma-mapping-common.h: In function â€˜dma_map_pageâ€™:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type â€˜voi
   d *â€™ used in arithmetic
   In file included from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:119,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-interface.c:26:
   include/linux/highmem.h: In function â€˜zero_user_segmentsâ€™:
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/.os-reg
   istry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Ii
   nclude  -I/usr/src/linux-headers-2.6.31-17-generic/arch/x86/include -include
   include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implic
   it-function-declaration -Wno-format-security -fno-delete-null-pointer-checks
   -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boun
   dary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstac
   k-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-
   unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=102
   4 -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdecla
   ration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cf
   i-asm -I/tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv -Wall -Wimpl
   icit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpoint
   er-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-
   qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"190.53\" 
   -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=
   KBUILD_STR(os_registry)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/
   selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/.tmp_os-registry.o /tmp/s
   elfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-registry.c:15:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜set_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type â€˜void *â€™ used in arithmetic
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜clear_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type â€˜void *â€™ used in arithmetic
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜change_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type â€˜void *â€™ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-registry.c:15:
   include/linux/prefetch.h: In function â€˜prefetch_rangeâ€™:
   include/linux/prefetch.h:57: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-registry.c:15:
   include/linux/sched.h: In function â€˜object_is_on_stackâ€™:
   include/linux/sched.h:2185: warning: pointer of type â€˜void *â€™ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-registry.c:15:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/io.h: In funct
   ion â€˜writeqâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type â€˜void *â€™ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-registry.c:15:
   include/linux/scatterlist.h: In function â€˜sg_virtâ€™:
   include/linux/scatterlist.h:199: warning: pointer of type â€˜void *â€™ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-registry.c:15:
   include/asm-generic/dma-mapping-common.h: In function â€˜dma_map_pageâ€™:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type â€˜voi
   d *â€™ used in arithmetic
   In file included from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:119,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/os-registry.c:15:
   include/linux/highmem.h: In function â€˜zero_user_segmentsâ€™:
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/.nv-i2c
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iinclud
   e  -I/usr/src/linux-headers-2.6.31-17-generic/arch/x86/include -include incl
   ude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-p
   rototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-f
   unction-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2
   -m32 -msoft-float -mregparm=3 -freg-struct-return -mprefer
   red-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffrees
   tanding -fstack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno
   -asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-l
   arger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclar
   ation-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi
   -asm -I/tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv -Wall -Wimpli
   cit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointe
   r-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-q
   ual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"190.53\" -
   UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=K
   BUILD_STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz
   2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/.tmp_nv-i2c.o /tmp/selfgz2004/N
   VIDIA-Linux-x86-190.53-pkg1/usr/src/nv/nv-i2c.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜set_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type â€˜void *â€™ used in arithmetic
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜clear_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type â€˜void *â€™ used in arithmetic
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜change_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type â€˜void *â€™ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/linux/prefetch.h: In function â€˜prefetch_rangeâ€™:
   include/linux/prefetch.h:57: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/linux/sched.h: In function â€˜object_is_on_stackâ€™:
   include/linux/sched.h:2185: warning: pointer of type â€˜void *â€™ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/io.h: In funct
   ion â€˜writeqâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type â€˜void *â€™ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/linux/scatterlist.h: In function â€˜sg_virtâ€™:
   include/linux/scatterlist.h:199: warning: pointer of type â€˜void *â€™ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/asm-generic/dma-mapping-common.h: In function â€˜dma_map_pageâ€™:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type â€˜voi
   d *â€™ used in arithmetic
   In file included from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:119,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/linux/highmem.h: In function â€˜zero_user_segmentsâ€™:
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/.nvacpi
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iinclud
   e  -I/usr/src/linux-headers-2.6.31-17-generic/arch/x86/include -include incl
   ude/linux/autoconf.h -Iubuntu/include  -D
   __KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-alia
   sing -fno-common -Werror-implicit-function-declaration -Wno-format-security 
   -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-stru
   ct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune
   =generic32 -ffreestanding -fstack-protector -fstack-protector-all -pipe -Wno
   -sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -m
   no-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibl
   ing-calls -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overfl
   ow -fno-dwarf2-cfi-asm -I/tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/sr
   c/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wpa
   rentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-c
   ompare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_S
   TRING=\"190.53\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D
   "KBUILD_BASENAME=KBUILD_STR(nvacpi)"
     -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2004/NVIDIA-Linux-
   x86-190.53-pkg1/usr/src/nv/.tmp_nvacpi.o /tmp/selfgz2004/NVIDIA-Linux-x86-19
   0.53-pkg1/usr/src/nv/nvacpi.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nvacpi.c:15:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜set_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type â€˜void *â€™ used in arithmetic
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜clear_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type â€˜void *â€™ used in arithmetic
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜change_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type â€˜void *â€™ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/linux/prefetch.h: In function â€˜prefetch_rangeâ€™:
   include/linux/prefetch.h:57: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:21,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/linux/sched.h: In function â€˜object_is_on_stackâ€™:
   include/linux/sched.h:2185: warning: pointer of type â€˜void *â€™ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nvacpi.c:15:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/io.h: In funct
   ion â€˜writeqâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type â€˜void *â€™ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/linux/scatterlist.h: In function â€˜sg_virtâ€™:
   include/linux/scatterlist.h:199: warning: pointer of type â€˜void *â€™ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:92,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/asm-generic/dma-mapping-common.h: In function â€˜dma_map_pageâ€™:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type â€˜voi
   d *â€™ used in arithmetic
   In file included from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-linux.h:119,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/linux/highmem.h: In function â€˜zero_user_segmentsâ€™:
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
     ld -m elf_i386   -r -o /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/sr
   c/nv/nvidia.o /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/nv-ker
   nel.o /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/nv.o /tmp/self
   gz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/nv_gvi.o /tmp/selfgz2004/NVID
   IA-Linux-x86-190.53-pkg1/usr/src/nv/nv-vm.o /tmp/selfgz2004/NVIDIA-Linux-x86
   -190.53-pkg1/usr/src/nv/os-agp.o /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg
   1/usr/src/nv/os-interface.o /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr
   /src/nv/os-registry.o /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nv-i2c.o /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/u
   sr/src/nv/nvidia.ko;) > /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src
   /nv/modules.order
   make -f /usr/src/linux-headers-2.6.31-17-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.31-17-generic/Modu
   le.symvers -I /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/Module
   .symvers  -o /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/Module.
   symvers -S -K /usr/src/linux-headers-2.6.31-17-generic/Module.markers -M /tm
   p/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/Module.markers -w  -s
   WARNING: could not find /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src
   /nv/.nv-kernel.o.cmd for /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/sr
   c/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/.nvidia
   .mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iin
   clude  -I/usr/src/linux-headers-2.6.31-17-generic/arch/x86/include -include 
   include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implic
   it-function-declaration -Wno-format-security -fno-delete-null-pointer-checks
   -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boun
   dary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32
    -ffreestanding -fstack-protector -fstack-protector-all -pipe -Wno-sign-comp
   are -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -
   Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls 
   -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dw
   arf2-cfi-asm -I/tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv -Wall
   -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -
   Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno
   -cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"190
   .53\" -UDEBUG -U_DEBUG -DNDEBUG  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBU
   ILD_STR(nvidia.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -DMODULE -c -o 
   /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/nvidia.mod.o /tmp/se
   lfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/nvidia.mod.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/percpu.h:45,
                    from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/current.h:5,
                    from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/incl
   ude/asm/processor.h:15,
                    from include/linux/prefetch.h:14,
                    from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nvidia.mod.c:1:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜set_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type â€˜void *â€™ used in arithmetic
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜clear_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type â€˜void *â€™ used in arithmetic
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h: In f
   unction â€˜change_bitâ€™:
   /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type â€˜void *â€™ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/n
   v/nvidia.mod.c:1:
   include/linux/prefetch.h: In function â€˜prefetch_rangeâ€™:
   include/linux/prefetch.h:57: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
     ld -r -m elf_i386  --build-id -o /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-p
   kg1/usr/src/nv/nvidia.ko /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/sr
   c/nv/nvidia.o /tmp/selfgz2004/NVIDIA-Linux-x86-190.53-pkg1/usr/src/nv/nvidia
   .mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 No such device
-> Kernel messages:
   [   27.174550] __ratelimit: 3 callbacks suppressed
   [   27.174560] type=1505 audit(1263823839.418:12):
   operation="profile_replace" pid=781
   name=/usr/share/gdm/guest-session/Xsession
   [   27.177352]   alloc irq_desc for 16 on node -1
   [   27.177361]   alloc kstat_irqs on node -1
   [   27.177378] EMU10K1_Audigy 0000:00:09.0: PCI INT A -> GSI 16 (level, low)
   -> IRQ 16
   [   27.214222] type=1505 audit(1263823839.458:13):
   operation="profile_replace" pid=782 name=/sbin/dhclient3
   [   27.214876] type=1505 audit(1263823839.458:14):
   operation="profile_replace" pid=782
   name=/usr/lib/NetworkManager/nm-dhcp-client.action
   [   27.215247] type=1505 audit(1263823839.458:15):
   operation="profile_replace" pid=782
   name=/usr/lib/connman/scripts/dhclient-script
   [   27.306743] type=1505 audit(1263823839.550:16):
   operation="profile_replace" pid=785 name=/usr/bin/evince
   [   27.382114] type=1505 audit(1263823839.626:17):
   operation="profile_replace" pid=785 name=/usr/bin/evince-previewer
   [   27.589789] type=1505 audit(1263823839.834:18):
   operation="profile_replace" pid=785 name=/usr/bin/evince-thumbnailer
   [   27.669438] type=1505 audit(1263823839.914:19):
   operation="profile_replace" pid=850 name=/usr/lib/cups/backend/cups-pdf
   [   27.670251] type=1505 audit(1263823839.914:20):
   operation="profile_replace" pid=850 name=/usr/sbin/cupsd
   [   27.702197] type=1505 audit(1263823839.946:21):
   operation="profile_replace" pid=851 name=/usr/sbin/tcpdump
   [   27.740334] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ
   16
   [   27.741238] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.13  Thu
   Jun 25 18:42:21 PDT 2009
   [   29.368487] agpgart-via 0000:00:00.0: AGP 2.0 bridge
   [   29.368518] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
   [   29.368614] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
   [ 1576.233883] NVRM: The NVIDIA GeForce2 MX/MX 400 GPU installed in this
   system is
   [ 1576.233889] NVRM:  supported through the NVIDIA 96.43.xx Legacy drivers.
   Please
   [ 1576.233892] NVRM:  visit http://www.nvidia.com/object/unix.html for more
   [ 1576.233896] NVRM:  information.  The 190.53 NVIDIA driver will ignore
   [ 1576.233899] NVRM:  this GPU.  Continuing probe...
   [ 1576.233914] NVRM: No NVIDIA graphics adapter found!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by fishkid257936 on 2010-01-18
Installed all of the programs, works great, but still no Window decorator.

---

### Post by djamu on 2010-01-18
> **fishkid257936 said:**
> um.. ok, after I kill, I see a blank screen. I searched online and people were saying remove a line from /boot/grub/menu.lst. My system does not even have this file. I want to be able to install the latest driver!

Did you properly read what I wrote ?
**/boot/grub/menu.lst has nothing !! to do with your driver**
do you mind giving me that link where you saw that ?
( most likely a very old post you read for changing ACPI )

also **ubuntu 9.10 is using grub2** > there's no more /boot/grub/menu.lst ( it still might be there after an upgrade from a previous version )

Also I did ask you to provide me some more info... 
It would be nice it you'd do so, saves me some time quessing.
mmmm 
It seems you're using quite an old card ( geforce2 MX ), I doubt it even supports composition. ( linux itself will run fine though )

I can't help you in this thread > ask in the appropriate one, your problem has nothing to do with the current topic here, Me ( or someone else ) might help you there,
but in any case using such an old card will severely limit your options.

from the sparse info you gave, following thread might help you 
[http://swiss.ubuntuforums.org/showthread.php?p=8604962](http://swiss.ubuntuforums.org/showthread.php?p=8604962)

good luck

---

### Post by fishkid257936 on 2010-01-23
Ok, I reloaded Ubuntu 9.10 and I told it to recreate the file with ```
sudo nvidia-xconfig
```. Then I saved the new one. THEN, I went to the Compiz Wiki and went under trouble shooting and this is what I saw, 
```
With _nvidia_ drivers earlier than version 100.14.09 drivers, you may not be able to see any window borders. To fix the problem, either run the following command: 
[CODE]sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```[/CODE]
I put in this code, restarted, and FINALLY IT WORKED!
Thanks for the help anyway!

---

### Post by puggle on 2010-01-24
I also had the same problems as many others here, but after following directions here was able to get nvidia x server settings to finally save to xorg.conf, with the resolution I want to use, 1152x864. But like you, on every reboot it resets to a lower resolution (800x600). I may have the same problem that you discovered - gnome x settings overwriting the nvidia settings. Unfortunately, I'm still fairly new to ubu, did some searches and tried to figure out on my own how to change those settings, but not able to figure it out. Can you point me to the correct file to edit? I thought it might be gnome-display-properties, but when I run that it wants me to use the nvidia utility instead.

Also, I know I have seen threads about issues similar to this before, and will do some searches again, but since I am posting now and it is related - I have an old CRT monitor that doesn't get detected correctly, so nvidia x server settings doesn't present me with the correct resolution and refresh combinations. Here are the monitor's specs:

Max Resolution 1600 x 1200 / 77.0 Hz
Max Sync Rate (V x H) 180.0 Hz x 97.0 KHz
Factory Preset Resolution Modes 1600 x 1200 / 77.0 Hz , 1280 x 1024 / 90.0 Hz , 800 x 600 / 149.0 Hz , 1024 x 768 / 118.0 Hz 

After nvidia writes the xorg.conf, I have this:

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

The only options that nvidia x server settings gives me (I'll skip everything below 800x600) are:
800x600     Auto, 72Hz, 60Hz, 56Hz
1024x768   Auto, 60Hz
1152x864   Auto, 60Hz
1360x768   Auto, 60Hz

The 1152x864 resolution is about right for me, but the 60Hz is very hard on my eyes. I used to run Windows with this monitor at 1024x768 or higher, and refresh around 75 or 80, and it was fine.

I tried manually editing the HorizSync value for my monitor in the xorg.conf, but it didn't help. (Do I need to be restarting a service each time I manually edit xorg.conf?) I also had the line

    Option         "metamodes" "1152x864_60 +0+0; nvidia-auto-select +0+0"

I tried changing the 60 to 75, but it rewrites it and adds the line

# Removed Option "metamodes" "1152x864_75 +0+0; nvidia-auto-select +0+0"

When I first switched to ubu, I had an Intel graphics adapter (now I have GeForce8100), and I was able to follow some posts I had found to manually edit my xorg.conf and got it to allow me to use a higher refresh. But I was faking it, and my xorg.conf probably ended up a lot uglier than it should have been. Here's what I had ended up with then for the Monitor and Screen sections:

Section "Monitor"
Identifier "ViewSonic"
VendorName "ViewSonic"
ModelName "PF790"
HorizSync 24.0 - 82.0
VertRefresh 50.0 - 85.0
EndSection

Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "ViewSonic"
SubSection "Display"
Viewport 0 0
Depth 1
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 4
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 8
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 15
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 16
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
EndSection

I'm thinking I need to do something similar now to get the higher refresh rate option, but I'm worried that it might make the nvidia driver mad if I don't know what I'm doing. Also, unless I resolve the issue that the gnome settings seem to be overwriting the nvidia settings, it will probably get worse.

Can anyone help? Thanks!


> **cybrid said:**
> This is "funny" I was having the same problem you all have had on an old machine of mine (Pentium IV + 6800XT) and after applying your solution I got a "working" xorg.conf, and I say working between quotes because every time I restart I still get 1024x768 instead of the 1680x1050 configured in the conf file, any ideas on this?

This is my current xorg.conf :

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Fri Aug 14 17:54:58 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Unknown"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1680x1050_60 +0+0; nvidia-auto-select +0+0; 1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```P.S: Please, If somebody could help me; this is really urgent

Edit:

Ok, it's almost 7 am now but I managed to fix it. It happened that on top of the problem described here, after getting a working xorg.conf, the gnome x settings had kept the old resolution and they were overwriting the nvidia settings. I just had to change the resolution in the gnome settings for it to work.

Also, I think this should be a how-to. In my search over the net on how to solve this issue I've found out that there seems to be quite a few people suffering from this.

---

### Post by Imune on 2010-01-27
Thanks MountainX, today is my first non-Windows day and thanks to you and all the others on this forum I got Ubuntu working with 2 screens on 2 graphic cards @ extra settings!

---

### Post by bhencetotozo on 2010-02-07
> **alexpw said:**
> I also received this error.

```

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
At least one Device section is required

```To fix it, I did the following:

```

root@myubuntu:~# mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
root@myubuntu:~# touch /etc/X11/xorg.conf 

```

I then copied ONLY the "Device" section from the backup to the new conf, since that is what it said was required.  Mine was as follows:

```

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

```

I then ran nvidia-settings and saved successfully.

Yoohoo !!!! 
1 Problem ... I cannot see Close, Minimize, Maximize buttons while in 16 bit color depth ... BUT the xorg file could atleast be written


I had Gutsy 7.10, and I never had this problem ...

now with 9.10, I have a few problems... Cannot isntall xmms NOR could safe the Nvidia config file... Im glad you guys helped me .. But why cant I see buttons on 16 Depth mode :'(

A+ A+ thank u so much guys.

---

### Post by JimmyANelson on 2010-03-02
[SIZE=4]_**!!FIXED in Ubuntu 9.10!!**_[/SIZE]

ERROR -> "Failed to parse existing X config file '/etc/X11/xorg.conf'!"

Alrighty this is what I did to fix it..seems to be working now


(Simple Version)

1) sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2)  sudo nvidia-settings
3)Click "Save Configuration"
4)Click "Save Preview"
5)Copy text from preview
6)sudo gedit /etc/X11/xorg.conf
7)Paste info from Preview and save
8)Restart to test



(Extended Version)

1>  open a terminal

2)  sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
     rename the xorg.conf file...well I don't know why..but it a good idea to save stuff right?

3) next enter the Nvidia Settings and click the "Save Configuration" button that gave you the error

4) it should pop up with something that is essentially asking where the file you just renamed is..

5)Click the "Show Preview" button select and copy the info

6) open the terminal

7) sudo gedit /etc/X11/xorg.conf
this creates a new "xorg.conf" file and opens it with gedit
needs to be edited in sudo mode--The "etc" directory is normally "read only"

8) Paste info from "Show Preview" 

9) Save the file and you're done

10) Restart to test

---

### Post by labinnsw on 2010-03-06
> **coolnezz said:**
> Thank you, this worked for me.
I can't believe Ubuntu is still as buggy as crap!
Even a simple file sharing still gives some error!
It still aint ready for primetime like M$!
pissing me off right now, it's 4:30AM!
----------------------------------------------------------------

Come on. With the amount of money poured into M$ it should not even be compared with Ubuntu. Doing so emphasizes the quality of Ubuntu and the lack thereof in M$. Good examples of what large sums of money should do are Google and Apple.

---

### Post by Gravata on 2010-03-12
> **norwoods said:**
> run sudo nvidia-xconfig to create a new Xorg.conf.

if there is a problem with this, rename Xorg.conf and run sudo nvidia-xconfig.
That worked !! Thanks a lot !

---

### Post by vahnx on 2010-03-23
It's reasons like this why Linux will never take off on the desktop.

---

### Post by AlexanderDGreat on 2010-03-24
> Best method is to get things working:

remove any old xorg.conf / xorg.conf.backup
Code:

sudo rm /etc/X11/xorg.conf
sudo rm /etc/X11/xorg.conf.backup

create new clean xorg.conf
Code:

sudo nvidia-xconfig

modify & Save to X Configuration File> uncheck merge
Code:

sudo nvidia-settings

Obviously this requires you to install the nvidia drivers & reboot first. this worked like a charm!

---

### Post by SiouxerBrewer on 2010-03-24
> **gslo said:**
> Thank's works for me too!

+1  Thank you!

---

### Post by icywind335 on 2010-03-25
Those steps or possible solution are not possible for me... Please help!

edit:
Oh it's working now!

---

### Post by oldunixguy on 2010-04-22
I am running ubuntu 9.10 64 bit with nVidia Geforce 9400GT.

I have tried ALL of the proposed methods to cure this but it still reports errors and does not update the file.

1. empty the /etc/X11/xorg.conf file
2. sudo nvidia-xconfig it reports:
[INDENT]Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  At least one Device section is required.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
[/INDENT]

3. sudo nvidia-settings
I select the 2nd monitor (disabled) and select Configure and then Separate X screen and OK. Then I do a save to X config file. This is the Preview:

[INDENT]# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@platinum)  Fri Apr  9 17:47:53 UTC 2010

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Wed Dec  9 16:34:26 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic"
    HorizSync       31.5 - 87.5
    VertRefresh     60.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "ViewSonic"
    HorizSync       31.5 - 93.8
    VertRefresh     60.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
[/INDENT]It has the Merge with existing file checked. Saving fails with "Unable to open /etc/X11/xorg.conf

If I try it without the Merge I get the same error.

If I copy the Preview and edit it into the /etc/X11/xorg.conf file and then run nvidia-settings I see no errors BUT the changes are not shown in the nvidia window. BUT when I try to save without making any changes to it I get the following errors:
[INDENT]Traceback (most recent call last):
  File "/usr/share/screen-resolution-extra/nvidia-polkit.py", line 75, in <module>
    operation_status = main(options)
  File "/usr/share/screen-resolution-extra/nvidia-polkit.py", line 51, in main
    exit_code = conf.backupAndWriteXorgConf([options.backup_filename, options.filename])
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 649, in _message_cb
    (candidate_method, parent_method) = _method_lookup(self, method_name, interface_name)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 244, in _method_lookup
    raise UnknownMethodException('%s is not a valid method of interface %s' % (method_name, dbus_interface))
UnknownMethodException: org.freedesktop.DBus.Error.UnknownMethod: Unknown method: backupAndWriteXorgConf is not a valid method of interface com.ubuntu.ScreenResolution.Mechanism


ERROR: Unable to open X config file '/etc/X11/xorg.conf' for writing.
[/INDENT]
This nvidia app USED to work some weeks ago while I only had one monitor. Recently, I noticed something odd during a normal ubuntu synaptic update where it updated the kernel (I think) and the nvidia stuff. Upon rebooting the display did NOT work. Some video recovery thing kicked in and asked if I wanted to go back to a previous video driver. I said yes and it rebooted and the display was OK. A friend thought there was some post about a kernel change that broke the latest nvidia driver and to fix it would require kernel src and recompile. I don't have that and am very new to ubuntu so I'm not wise enough to do that.

Today I plugged in a second monitor and wanted to get it running. This led me to the problems I describe here.

Help!

---

### Post by samzie on 2010-04-27
im new to linux and lovin it, ive tried to get both monitors working reading this thread but ultimatly i still get this error when i try to save, someone help me please as i have used to boxs of tissues crying:_

Failed to set MetaMode (1) 'CRT-0: nvidia-auto-select @1280x1024 +0+0, DFP-0: nvidia-auto-select @1920x1080 +1280+0' (Mode 3200x1080, id: 50) on X screen 0.

---

### Post by gregsmith_to on 2010-04-27
Didn't work for me. Same problem, 9.10 on 86_64, and 185.18.36 drivers. nvidia-settings choked on the empty file ('At least one Device section is required' to the tty and then segfaulted). Do you happen to know what it changed in the xorg.conf file so I can put it in myself?

---

### Post by DrDunkMcNally on 2010-05-06
> **scottac said:**
> I had a similar problem a while back. try this if you havent already

```
sudo nvidia-settings
```let me know how it goes


THANK YOU!! worked perfectly for me, allowed me to save the xconfig file and I can now switch users without needing to re-configure my x screens.  Thanks a million! 
Running: ubuntu Karmic on HP Pavillion dv6675US

You're a headache saver.

-dunk

---

### Post by PrimaryMaster on 2010-06-12
I used ajayrockrock's solution above, with a  twist.

1) open a terminal
2) sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2) sudo touch /etc/X11/xorg.conf
3) sudo nvidia-settings
4) hit "save configuration"

Now "hit save" would still not work on my Lenovo S12 Ion netbook but I could see the preview file. I copy the contents of the previewed xorg.conf to my clipboard and continue after step 3:

quit nvidia-settings

gksudo nautilus 

go to etc/X11/xorg.conf, right click and gedit it. 

paste the preview file's contents here, save and close. 

----

Thank you for your support guys :D

---

### Post by iriber on 2010-09-27
try this:

1) backup and remove xorg.conf
[COLOR=black][COLOR=#008000]cd /etc/X11 [/COLOR][/COLOR]
 [COLOR=black][COLOR=#008000]sudo mv xorg.conf xorg.conf.backup[/COLOR][/COLOR]
 [COLOR=black][COLOR=#008000]sudo nvidia-xconfig[/COLOR][/COLOR]
 [COLOR=black][COLOR=#008000]cd /etc/X11[/COLOR][/COLOR]
 [COLOR=black][COLOR=#008000]sudo rm xorg.conf[/COLOR][/COLOR]

[COLOR=#008000][/COLOR]
2) configure your screen

[COLOR=#008000]gksudo nvidia-settings[/COLOR]
[COLOR=#008000]
[/COLOR]
3) save to X configuration file at:
[COLOR=#008000]/etc/X11/xorg.conf[/COLOR]
 
[COLOR=#008000][/COLOR]
enjoy!

---

### Post by covenist5 on 2011-05-28
I've tried the steps outlined in this thread, and still no luck.  I've moved the xorg.conf file to xorg.conf.backup, touch'ed /etc/X11/xorg.conf , and ran (sudo) nvidia-settings, but when I tried to save my settings, it still "failed to parse /etc/X11/xorg.conf" 

I have been looking for a solution for this issue for quite awhile, to the point where I've lost track of how many things I've tried.

I had to manually set the default resolution, by editing the .....can't remember filename.... under either "display" or "screen"  (screen i think)  While I've thought of changing the 1024x768 to2048x768, but I want to be able to watch media on my tv in fullscreen without having to resize the totem window every time.  any help would be greatly appreciated.

Thank you in advance

---

### Post by covenist5 on 2011-05-30
It works now! I had to retry when I was calm and not frustrated.  Thank you very much.

---

### Post by Berg96 on 2011-06-12
I'm very new to linux, and am also trying to install my nvidia drivers, but it fails everytime. I tried using your steppes, but i get the same result. Am i doing something wrong? All i did was paste the lines into the terminal. I woud greatly appreciate any help.

Oops, I clicked my browser one page to far back, I didn't intend on posting here. So sorry.

---

### Post by Berg96 on 2011-06-12
I'm very new to linux, and I'm trying to get my nvidia drivers to work. Sadly those steppes don't work for me, it's exactly the same when i reboot. All i did was paste the lines into a terminal windows. Am i doing something wrong or what?

---

### Post by TheSurak on 2011-10-21
Just found this on another thread - you must install python-gtk2. Try running from a terminal:

sudo apt-get install python-gtk2

I guess most of you guys are using KDE, too. Well apparently nvidia-settings uses python-gtk to ask for your password to write xorg.conf with root permissions AND this does NOT work with KDE, unless you install the python-gtk2 package.

This is a better solution because you don't need to run the whole nvidia-settings program as root, just type the password to write the file with root permissions. This will also solve similar issues with other programs that use python-gtk2.

Hope this helps.

---

### Post by ka55o5 on 2013-04-20
[color=gray]** I **_KNOW_** this is a stale, old thread, bear with me please, if you will, as it comes up w/Google query "nvidia-settings save file location" && ***many*** others. **[/color]

> **TheSurak said:**
> This is a better solution because you don't need to run the whole nvidia-settings program as root, just type the password to write the file with root permissions.
Yes, ofc. The reason I'm posting here, however, is because many users/posts said to run nvidia-settings with sudo, instead of using gksu; [which is a must]("https://help.ubuntu.com/community/RootSudo"):

> You should **never** use normal sudo to start graphical applications as root.```
https://help.ubuntu.com/community/RootSudo
```

PS.
> **TheSurak said:**
> [..] you must install python-gtk2.
sudo apt-get install nvidia-common will take care of ALL that.

---

### Post by poltiser on 2013-04-21
There is a problem with NVIDIA driver for many years. I deal with it copying same xorg.conf file for more than 6 years already. That nvidia-settings is saving anything in conf file it is an illusion. It always goes back to settings pre-set in installer and for unknown reason does not reflect changes which are so promising available in nvidia-settings program. One can choose better resolution, better quality, sharpening etc. - first - it is not reflected in settings, it is not included in future restarting a driver in next reboot. Is it an advertising gimmick? I like Ubuntu more than MSW. There are those little imperfections which annoying people, can make them go elsewhere... Do what promised or do not promise at all!

On practical note, I would be very grateful for explanation how to correct nvidia-settings and permanently change them to desired values? But in easy xorg.conf example? Do I need to change different file as well?

---


---
title: "VEC Footpedal for transcription, mapping hot-keys?"
date: 2014-07-03
forum: Hardware
---

### Post by matt116 on 2014-07-03
I have a 3-button Infinity foot pedal, that is being used for transcription with NCH Express Scribe. But, sadly, NCH does not support video playback on their Linux software. So I was looking into using VLC for my transcribing as a lot of people have had success using these pedals with VLC in Windows. But even with Express Scribe seeing and customizing  the pedal, I can not get any other program to see the pedal. VLC does not see the pedal to remap the hot-keys. And I have tried AutoKey for remapping and scripting, and even that did not see the pedal. I am trying to find a pedal utility or driver to make Xubuntu 14.04 see the pedal "globally" and not just in the one program. FootPedal Utility from the software market is an abandoned, non-functioning, dead end. Any ideas?

---

### Post by gungadin2 on 2014-09-01
Hi Matt
I hope this helps
```
#!/usr/bin/python
# A big shout out to [email]kostmo@gmail.com[/email] who started footpedal ([https://code.google.com/p/footpedal/](https://code.google.com/p/footpedal/)) but appears never to have finished it
# certainly there is no configuration available as everything is hard coded and there is a lot of fiddling about with releasing keys
# which is superfluous as the infinity pedal does appear to send codes on pedal release but that said kostmo's code is proper python code
# as opposed to this hack of a script
#
# This python script was written specifically to run under Linux using VLC as the media player and LibreOffice Writer as the word processor
# Written on a Linux Mint Qiana 32bit machine
# to launch this from the desktop the command is: python $HOME/foot.py (if you installed it in your HOME directory)
# and you will need to have installed xterm (use synaptic to install it)
#
# You can run the program with a single parameter (i.e. python $HOME/foot.py transcription) which will be accepted as the section name
# for the footpedal.conf file or run with no  parameter and it will use "default" as the section name
# The footpdeal.conf file is stored in $HOME/footpedal ($HOME/footpedal/footpedal.conf)
# example footpedal.conf
#
#        # footpedal default configuration file
#        # format
#        # [ "section name" ]
#        # HID_FILE_ID = whatever /dev/usb/hiddev you are using
#        # Pedal definitions # comment
#
#        [ "default" ]
#
#        HID_FILE_ID = /dev/usb/hiddev0
#        LEFT_PEDAL = XF86Switch_VT_10 # Reverse F10 Function Key
#        MIDDLE_PEDAL = XF86AudioPlay  # Play/Pause button
#        RIGHT_PEDAL = XF86AudioNext   # Forward
#
#        [ "transcription" ]
#
#        HID_FILE_ID = /dev/usb/hiddev1
#        LEFT_PEDAL = XF86Switch_VT_11 # F11 function key
#        MIDDLE_PEDAL = XF86AudioPlay  # Play/Pause key
#        RIGHT_PEDAL = XF86AudioPlay   # Play/Pause as well - because the Infinity footpedal is too small
#
#        #End of configuration file
#
# You may also have to install ConfigObj into python (use synaptic to install it)
#
# You will need to define your global keys in VLC media player to the keys that you define in the configuration file footpedal.conf
#
# Remember to ensure that if those keys are used in LibreOffice to disable them
#
# If you choose to use F10 as per the example conf file, disable F10 in Terminal
# (Edit - keyboard shortcuts - disable Menu shortcut key (F10 by default) ) 
#
# Remember to create a /etc/udev/rules.d/footpedal.rules file to override the permissions issue on the /dev/usb/hiddev(n) file
# It should contain the following
# "ACTION=="add", SUBSYSTEMS=="usb", ATTRS{idVendor}=="05f3", ATTRS{idProduct}=="00ff", MODE="660", GROUP="plugdev"
# and add foot.py users to the group plugdev
# NB the ATTRS{idVendor}=="05f3", ATTRS{idProduct}=="00ff" is specifically for the Infinity USB footpedal use lsusb to see the
# vendor and product codes for your device if it isn't from Infinity
#
# Stop the program with Ctrl C
#
# Finally, I am sure that a real python programmer could do a better job than this but as I am not,
# this is my best shot and at least it works (for me :) )
#
import os, sys
configuration_dir = os.environ["HOME"]
from configobj import ConfigObj
config_filename = configuration_dir + "/footpedal/footpedal.conf"
# the following test for the configuration file could be done with ConfigObj (validate) but this seemed simpler
try:
    cfg = open(config_filename,"r")
except IOError:
        print ("Config: " + configuration_dir + "/footpedal/footpedal.conf missing - Closing down")
        exit(1)
cfg.close

# Process the configuration file
# Define the default section or accept the section name from the command line

config_section = "default"
narg = len(sys.argv)
if narg > 1:
    if sys.argv[1]:
        config_section = sys.argv[1]
cfg = ConfigObj(config_filename)

#define values to use from the configuration file
hidfile = cfg[config_section]["HID_FILE_ID"]
left_key = cfg[config_section]["LEFT_PEDAL"]
middle_key = cfg[config_section]["MIDDLE_PEDAL"]
right_key = cfg[config_section]["RIGHT_PEDAL"]
#Print out the device file being used and the values of the pedals
if narg > 1:
    print ("Using " + sys.argv[1] + " as the section of the configuration file")
else:
        print ("Using default as the section of the configuration file")
print ("Pedal device file is " + hidfile)
print ("Left Pedal Sends " + left_key)
print ("Middle Pedal sends " + middle_key)
print ("Right Pedal sends " + right_key)
print ("Running......")
# Open the footpedal for input
try:
            hidfile = open(hidfile)
except IOError:

            msg = "You need permission to access the device. Try creating a footpedal.rules file\n"
            msg += "in /etc/udev/rules.d with the following line in it\n"
            msg += '"ACTION=="add", SUBSYSTEMS=="usb", ATTRS{idVendor}=="05f3", ATTRS{idProduct}=="00ff", MODE="660", GROUP="plugdev"\n'
            msg += "Remember to add those users who will use the footpedal to the plugdev group\n"            
            msg += "The above line is specifically for the Infinity foot pedal, for anything else you should use the lsusb command\n"
            msg += "to get the vendor and product numbers"

            print(msg)
            exit(1)

#Define the footpedal as Non Blocking i.e. accept input without waiting for a carriage return
import fcntl
fd = hidfile.fileno()
fl = fcntl.fcntl(fd, fcntl.F_GETFL)
fl = fl | os.O_NONBLOCK
fcntl.fcntl(fd, fcntl.F_SETFL, fl)


# Keep reading the footpedal in a loop

while 1==1: # Endless loop
    pass # nested while loop to endlessly check for input from the pedal: Set it to zeros so that it is defined if nothing has been pressed
    hidstring = "0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0"
    while 1==1: # Endless loop
        try:
            hidstring = hidfile.read(24)
        except:
            import time
            time.sleep(0.05)
        break
    pedal_byte_values = map(ord, hidstring)
    # Split message into signals for each pedal
    pedal_signals = [pedal_byte_values[8*i:8*(i+1)] for i in range(3)]
    # the fifth byte holds 1 if the pedal has been pressed or 0 if not 
    pedal_state = [(signal[4]) for signal in pedal_signals]

# use the Linux xte command to issue a key press which will be picked up by VLC to control the audio 
    if pedal_state[0] == 1:
#        print ("LEFT")
        os.system( 'xte "key ' + left_key + '"')
    elif pedal_state[1] == 1:
#        print ("MIDDLE")
        os.system( 'xte "key ' + middle_key + '"')
    elif pedal_state[2] == 1:
#        print("RIGHT")
        os.system( 'xte "key ' + right_key + '"')
    else:
        continue


    continue

```



------------------- regards gungadin

---

### Post by gungadin2 on 2014-09-01
Matt
I noticed that the reply post has taken out the indents in the python script so you will have to put them back in.
Sorry about that but this is my first post and I don't know how to paste it with the indents in place.
Perhaps I can post the foot.py file as an attachment. I'm not sure
regards
Gungadin

---

### Post by lisati on 2014-09-01
> **gungadin2 said:**
> Matt
I noticed that the reply post has taken out the indents in the python script so you will have to put them back in.
Sorry about that but this is my first post and I don't know how to paste it with the indents in place.
Perhaps I can post the foot.py file as an attachment. I'm not sure
regards
Gungadin

I've wrapped your script with [noparse]```
 and 
```[/noparse], which should help preserve the indents for you.

---

### Post by gungadin2 on 2014-09-01
Thanks Lisati
As you might have guessed, I don't do forums much.
I appreciate your help and will keep in mind the  for code entries future reference
Regards
Gungadin

Since last year, I have developed 2 Linux transcription programs, both support Infinity USB foot pedal and both are integrated into Libreoffice.
footswitch2 uses VLC : - [https://sourceforge.net/p/footswitch2](https://sourceforge.net/p/footswitch2)
footswitch3 uses Gstreamer : - [https://sourceforge.net/p/footswitch3](https://sourceforge.net/p/footswitch3)
They are both free and you can check out the full documentation, at the above urls, before you make a decision to download or not.
Regards

---

### Post by leunam12 on 2015-10-25
Hi, I am having problems with this pedal as well, I have installed the python script and created the footpedal.rules file but I still get the permissions message when I run the script. I can run as root but not as my regular user.

Any help is appreciated.

Thank

---

### Post by gungadin2 on 2015-11-06
Hi leunam12
which script are you referring to, the one posted above or one of footswitch2 or footswitch3?
If it's the one posted above, that is state of the "Ark" and I'd recommend that you use one of the 2 links that I posted this August.
However, if you want to try the antique script,  suspect that you haven't added yourself to the "plugdev" group.
type in the following:
sudo adduser &#8220;yourusername&#8221; plugdev

that will add your username to the plugdev group which has permission to access the /dev/usb/hiddev(n) device that was specifed in the footswitch.rules file.

Either way, let me now how it goes.
It was sheer fluke, that I logged in to see your message, as I very rarely do.
I'll log in to check how your doing, every now and then for a week or two.

---

### Post by leunam12 on 2015-11-10
I added myself to the plugdev group and it still tells me that I need permission. I also added the file to /etc/udev/rules.d

The footswitch2 programs fails to install.

```
Selecting previously unselected package libreoffice-script-provider-python. 
(Reading database ...  dpkg: warning: files list file for package 'getdeb-repository' missing; assuming package has no files currently installed 
(Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 313684 files and directories currently installed.) 
Preparing to unpack .../libreoffice-script-provider-python_1%3a4.2.8-0ubuntu3_all.deb ... 
Unpacking libreoffice-script-provider-python (1:4.2.8-0ubuntu3) ... 
Selecting previously unselected package sqlite3. 
Preparing to unpack .../sqlite3_3.8.2-1ubuntu2.1_amd64.deb ... 
Unpacking sqlite3 (3.8.2-1ubuntu2.1) ... 
Processing triggers for man-db (2.6.7.1-1ubuntu1) ... 
Setting up libreoffice-script-provider-python (1:4.2.8-0ubuntu3) ... 
Setting up sqlite3 (3.8.2-1ubuntu2.1) ... 
Selecting previously unselected package footswitch2. 
(Reading database ...  dpkg: warning: files list file for package 'getdeb-repository' missing; assuming package has no files currently installed 
(Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 313698 files and directories currently installed.) 
Preparing to unpack .../footswitch2_2.0.0_all.deb ... 
Unpacking footswitch2 (2.0.0) ... 
Setting up footswitch2 (2.0.0) ... 
Unable to access the X Display, is $DISPLAY set properly? 
dpkg: error processing package footswitch2 (--install): 
 subprocess installed post-installation script returned error exit status 1 
Processing triggers for man-db (2.6.7.1-1ubuntu1) ... 
Processing triggers for mime-support (3.54ubuntu1.1) ... 
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ... 
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ... 
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ... 
Rebuilding /usr/share/applications/bamf-2.index... 
Errors were encountered while processing: 
 footswitch2
```

---

### Post by gungadin2 on 2015-11-11
Strange!
First off what is the result of running the command 
echo $DISPLAY
on your command line
second a few details of your setup
python version and Operating system
uname -a
 will give something like 
Linux pc64 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
python
 will give something like
Python 2.7.6 (default, Jun 22 2015, 17:58:13) 
[GCC 4.8.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
Use Ctrl/d to exit

plus the command that you are using to install the program

---

### Post by leunam12 on 2015-11-11
The result of echo $DISPLAY is :0.0
```
rivasdom@RivasPC-2:~$ uname -a
Linux RivasPC-2 3.13.0-67-generic #110-Ubuntu SMP Fri Oct 23 13:24:41 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

```
rivasdom@RivasPC-2:~$ python
Python 2.7.6 (default, Jun 22 2015, 17:58:13) 
[GCC 4.8.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

I'm using the Software Center to install the program.

Thanks

---

### Post by gungadin2 on 2015-11-11
I have never used the software center, as you have to manually download the footswitch2 and footswitch3 packages.
use gdebi the debian package installation tool by clicking on the package file footswitch2_2.0.0_all.deb
or
preferably, because we get a full activity listing
 on the command line 
sudo dpkg -i footswitch2_2.0.0_all.deb

Your linux, python and $DISPLAY as :0.0 look fine
if after trying
sudo dpkg -i footswitch2_2.0.0_all.deb
you still get an error try setting DISPLAY=:0 and then sudo dpkg again
post a full listing of the command and results, if there is still a problem

---

### Post by leunam12 on 2015-11-11
The way I use the Software Center to install is by downloading the file and double-clicking on it and the Software Center pops up and takes it from there. I will try the command line when I get home. Thank you.

---

### Post by leunam12 on 2015-11-12
```

rivasdom@RivasPC-2:~/Downloads$ sudo dpkg -i footswitch2_2.0.0_all.deb 
Swipe your finger across the fingerprint reader
Selecting previously unselected package footswitch2.
dpkg: warning: files list file for package 'getdeb-repository' missing; assuming package has no files currently installed
(Reading database ... 313684 files and directories currently installed.)
Preparing to unpack footswitch2_2.0.0_all.deb ...
Unpacking footswitch2 (2.0.0) ...
dpkg: dependency problems prevent configuration of footswitch2:
 footswitch2 depends on libreoffice-script-provider-python; however:
  Package libreoffice-script-provider-python is not installed.
 footswitch2 depends on sqlite3; however:
  Package sqlite3 is not installed.

dpkg: error processing package footswitch2 (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Errors were encountered while processing:
 footswitch2
rivasdom@RivasPC-2:~/Downloads$ sudo apt-get install libreoffice-script-provider-python
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 footswitch2 : Depends: sqlite3
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
```

rivasdom@RivasPC-2:~/Downloads$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-script-provider-python sqlite3
Suggested packages:
  sqlite3-doc
The following NEW packages will be installed:
  libreoffice-script-provider-python sqlite3
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 58.9 kB of archives.
After this operation, 384 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libreoffice-script-provider-python all 1:4.2.8-0ubuntu3 [30.1 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main sqlite3 amd64 3.8.2-1ubuntu2.1 [28.8 kB]
Fetched 58.9 kB in 0s (141 kB/s)  
Selecting previously unselected package libreoffice-script-provider-python.
dpkg: warning: files list file for package 'getdeb-repository' missing; assuming package has no files currently installed
(Reading database ... 313908 files and directories currently installed.)
Preparing to unpack .../libreoffice-script-provider-python_1%3a4.2.8-0ubuntu3_all.deb ...
Unpacking libreoffice-script-provider-python (1:4.2.8-0ubuntu3) ...
Selecting previously unselected package sqlite3.
Preparing to unpack .../sqlite3_3.8.2-1ubuntu2.1_amd64.deb ...
Unpacking sqlite3 (3.8.2-1ubuntu2.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up libreoffice-script-provider-python (1:4.2.8-0ubuntu3) ...
Setting up sqlite3 (3.8.2-1ubuntu2.1) ...
Setting up footswitch2 (2.0.0) ...

(python:5804): IBUS-WARNING **: The owner of /home/rivasdom/.config/ibus/bus is not root!
The user `rivasdom' is already a member of `plugdev'.
Adding user `rivasdom' to group `fuse' ...
Adding user rivasdom to group fuse
Done.
Adding user `josefina' to group `plugdev' ...
Adding user josefina to group plugdev
Done.
Adding user `josefina' to group `fuse' ...
Adding user josefina to group fuse
Done.

(python:5948): IBUS-WARNING **: The owner of /home/rivasdom/.config/ibus/bus is not root!
mv: cannot stat ‘/home/rivasdom/fs2.db’: No such file or directory

```

---

### Post by gungadin2 on 2015-11-12
"(python:5948): IBUS-WARNING **: The owner of /home/rivasdom/.config/ibus/bus is not root!
mv: cannot stat &#8216;/home/rivasdom/fs2.db&#8217;: No such file or directory"

Is that how it ended?
Did it install or not?
On my systems package dependencies are automatically installed. I don't have to install them manually. Perhaps that is just the way I set it up, I don't recall.
On running it, you should get a screen that firstly ensures that users are member of the group plugdev, it then moves on to identify your Infinity foot pedal.
Once that is complete, the program attempts to convert any existing footswitch database files, in case you are upgrading.
After this you should find Footswitch2 in your Audio/Video programs.
You can always manually run 
fs2
from the command line.
Your message above, doesn't suggest that you saw any of that, nor does it say whether the package installed or not, I'm assuming not.
It almost seems as if you have no X windows running.

1. Do you have wxpython-gtk2.8 installed?
2. What is that IBUS-Warning?
3. Can you run /usr/share/footswitch2/convertdb.py (from the command line) and see it open a Gui window
    Even if there is no existing database to copy, it will tell you that and output a message box.
4. After that can you run fs2 (from the command line)

---

### Post by leunam12 on 2015-11-12
I don't know if it installed. I can see it in the audio video menu but when I click on it it doesn't do anything.

1- I do not have wxpython-gtk2.8 installed. Should I install it? or go back, install it and then attempt to install footswitch2 again?
2- I don't know what is that IBUS warning.
3- I could run the command and the windows opened

4.```
rivasdom@RivasPC-2:~$ fs2
Traceback (most recent call last):
  File "/usr/bin/fs2", line 5259, in <module>
    Footswitch2(None)
  File "/usr/bin/fs2", line 78, in __init__
    self.config()
  File "/usr/bin/fs2", line 178, in config
    self.LibreOffice_Macros()
  File "/usr/bin/fs2", line 331, in LibreOffice_Macros
    Notify(None,"footswitch2", "Installing macros for LibreOffice") 
  File "/usr/bin/fs2", line 5183, in __init__
    self.timeout = notify_override
NameError: global name 'notify_override' is not defined

```

---

### Post by gungadin2 on 2015-11-13
Lord what a mess!
Normally a system, when installing a debian package will install all of the packages dependencies for you.
Yours, for whatever reason doesn't appear to have done that or even warn you that they are missing.
The dependencies for footswitch2 are as follows:
python (>= 2.7), python-configobj, vlc (>=2.1.4), libreoffice-writer (>=4.2), python3-uno, libreoffice-script-provider-python, python-wxgtk2.8, sqlite3, pulseaudio (>=4.0), fuse, gvfs, gvfs-backends, gvfs-bin, gvfs-fuse, sox
Use synaptic to check that they are installed and if not install them.
Then try reinstalling footswitch using the dpkg command.
It appears that at the moment footswitch is indeed installed but is missing one or more of its dependencies.
I'll have a dig about and see if I can find if there is a system setting that needs to be set to ensure that dependencies are loaded automatically.
Let me know how you get on.

*update on synaptic package installation*
Synaptic provides two methods for upgrading your system: 

[LIST]
[*]*Smart Upgrade (Dist-Upgrade)* -- *recommended* 
 The smart upgrade method tries to resolve package conflicts. This  includes installing additional dependencies (required packages) if  needed and preferring packages with higher priority. Smart Upgrade has  the same effect as the *apt-get dist-upgrade* tool on the command line. 
[*]*Default Upgrade* 
 The default upgrade method marks upgrades of installed packages only.  If the new version of a package depends on not installed packages or  coflicts with an already installed package, it will not be upgraded. 
[IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=info.png[/IMG] **Dist-upgrade** is the default upgrade method used by Synaptic. To change the upgrade method,  choose **Preferences** from the **Settings** menu, then click on the **General** tab and adjust the **System upgrade** entry. 

I think that this is the seat of your problem.
Update your pc to use smart upgrade or start using the apt-get dist-upgrade tool

Thinking about it (later) just install the debian installation tool 'gdebi' and install footswitch with that, because I am almost certain that gdebi does install all the dependencies but setting up synaptic (it's a front end for apt) to "smart upgrades" is still a good idea. 
[/LIST]

---

### Post by oulipian on 2016-01-28
Hi, I'm having similar problems installing Footswitch2 on Ubuntu. I've tried installing using gdebi, but get a popup with this error message:

> No existing Fs2 database to convert - Must be Initial Setup

and the following output from Terminal:

> (Reading database ... 229893 files and directories currently installed.)
Preparing to unpack footswitch2_2.0.0_all.deb ...
Unpacking footswitch2 (2.0.0) over (2.0.0) ...
Setting up footswitch2 (2.0.0) ...

(python:4903): IBUS-WARNING **: The owner of /home/barry/.config/ibus/bus is not root!
The user `barry' is already a member of `plugdev'.
The user `barry' is already a member of `fuse'.
Bus 007 Device 002: ID 05f3:00ff PI Engineering, Inc. VEC Footpedal

(python:4967): IBUS-WARNING **: The owner of /home/barry/.config/ibus/bus is not root!
mv: cannot stat &#8216;/home/barry/fs2.db&#8217;: No such file or directory
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...


Any help would be appreciated, thanks!

---

### Post by oulipian on 2016-02-12
I should have said before that I have all the dependencies installed but  get the same error messages as leunam12. Can anyone help? Thanks.

---

### Post by gungadin2 on 2016-03-13
Hi oulipian, sorry about the delay, Footswitch 2.0.0 had a bug related to the libreoffice macro installation, it has been replaced with footswitch 2.0.1 which should resolve that issue. However Footswitch2 version 3.0.0 is now available at [https://sourceforge.net/projects/footswitch2](https://sourceforge.net/projects/footswitch2) so I suggest that you load that instead, as it also makes the running of the libreoffice macros much simpler by removing a complicated set up step. Version 3 also allows you to use other foot pedals than the Vec Infinity foot pedal.

---

### Post by oulipian on 2016-03-13
That's great, thanks gungadin2!

---


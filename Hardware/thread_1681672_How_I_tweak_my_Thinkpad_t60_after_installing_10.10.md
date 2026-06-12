---
title: "How I tweak my Thinkpad t60 after installing 10.10"
date: 2011-02-04
forum: Hardware
---

### Post by kolinab on 2011-02-04
**Looking for info on a newer version of Ubuntu? Check here: [http://ubuntuforums.org/showthread.php?p=11334250#post11334250](http://ubuntuforums.org/showthread.php?p=11334250#post11334250)**

I am picky about getting everything running right when I upgrade my Ubuntu. I always choose a clean install and use a separate partition for my /home. When upgrading, I only keep data directories in my home partition - not application preferences.

I cannot take credit for any of the tweaks applied here - most solutions have been found either here, [Thinkwiki]("http://www.thinkwiki.org/wiki/Category:T60") or elsewhere on the web. Many adjustments require a restart to take effect and may not be the easiest of most elegant solutions, but they work for me. I try to present a command line solution where possible. Your suggestions are welcome.

Before upgrading, I first make a complete backup of my /home partition. Once or twice I have been thankful for it. Since I reinstall my applications, the only hidden folders I keep from my /home partition are ./mozilla, ./thunderbird, ./skype, ./local/share/tomboy, and ./config/tomboy. I don't mind reinstalling new software and setting up program preferences again. If you want to keep your preferences, you can safely leave the hidden directories on your /home partition alone.

**Tweaks applied to clean install of Ubuntu Maverick 10.10 on my IBM Thinkpad t60** (Type 2007-72U)

[U][B]Thinkpad specific modifications
[/B][/U][B]
1. Make the middle mouse button work as a scroll button with the trackpoint:[/B]

Configure as per "Configuration using udev and HAL" on: [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint). (Note the path difference between the solution for Lucid and Maverick.) Use the instructions using the xorg.conf.d method.

**2. Enable the volume control buttons:**

```
sudo gedit /etc/rc.local
```and add the line

```
cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask  /sys/devices/platform/thinkpad_acpi/hotkey_mask
```I read somewhere  that the volume buttons work out of the box but the on screen display  doesn't. Apparently this tweak just enables the on screen display.

**3. Enable Thinkpad Active Protection System**:

This is supposed to enable hard drive parking when the laptop is moved, as well as some other Thinkpad specific features.

```
sudo apt-get install hdapsd tp-smapi-dkms
```There seem to be many sets of instructions for enabling these features   and I don't understand them all. Testing my system shows the hard drive   parking feature seems to work properly.

**4. Map the ThinkVantage button to some useful function:** 

I use mine to launch a terminal window.

Go to: System . . . Preferences . . . Keyboard Shortcuts

Click Add . . . and name the button 'Launch Terminal.' In the 'command' box type: gnome-terminal

Now highlight this new entry (where it may read 'disabled'), then push the ThinkVantage button. This  should successfully map the button to launch a terminal window. You  could adapt this process  to launch any other application. 

**5. Enable receiving files over bluetooth and make bluetooth default to 'off' on startup:**

```
sudo apt-get install gnome-user-share
sudo gedit /etc/rc.local
```and add the line:

rfkill block bluetooth

Save and close.

Click the bluetooth icon in the taskbar, select 'Preferences,' click the 'Receive files' button, and check the box 'receive files in Downloads folder over bluetooth.'

_**Other Modifications:**_
[B]
6. Disable the 'drum' startup sound[/B]:

In nautilus, navigate to: filesystem/usr/share/sounds/ubuntu/stereo

Rename 'dialog-question.ogg' to 'DISABLEDdialog-question.ogg'

I do a ```
gksudo nautilus
``` in the terminal to get there.

Alternatively, using the command line:

```
sudo mv /usr/share/sounds/ubuntu/stereo/dialog-question.ogg /usr/share/sounds/ubuntu/stereo/DISABLEDdialog-question.ogg
```[B]

7. Install Firefox 4

[/B]```

sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get install firefox ubufox

```** 8. Remove the evolution envelope icon from the notifier applet:**

I don't want the envelope to own space in my panel.

```
sudo apt-get remove indicator-messages
killall gnome-panel
```[B]
9. Add the medibuntu repository[/B]:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list  http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list  && sudo apt-get --quiet update && sudo apt-get --yes  --quiet --allow-unauthenticated install medibuntu-keyring &&  sudo apt-get --quiet update
```I also add the libdvdcss2 and w32codecs packages:

```
sudo apt-get install libdvdcss2 w32codecs
```Read more about medibuntu [here]("https://help.ubuntu.com/community/Medibuntu").

**10. Install ubuntu-restricted-extras**:

```
sudo apt-get install ubuntu-restricted-extras
```Read more about ubuntu-restricted-extras [here]("https://help.ubuntu.com/community/RestrictedFormats").

**11. Change the login background image to your own:**

```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```Log out, then choose the background tab in 'Appearances' when it appears. Select the background you want (I use a black screen). Then log back in.

Next, to prevent the appearances dialog from appearing each restart,

```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```**12. Change the 'selected items' colour in the customisation tab of 'Appearance Properties' from orange to something nicer** (I use #5C87D6). Save the theme with your own name.

**13. Install Wine:**
 
 ```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.3
```[B]
14. Install other software:[/B]
 
 Enable the Ubuntu partners repository in Synaptic (needed later for Acrobat Reader and Skype):
 
 System . . . Administration . . . Synaptic Package Manager . . .   Settings . . . Repositories . . . 'Other Software' Tab . . . and click   'Canonical Partners.'
 
 These are some of my favourites:
 
 KeePassX
 Gimp
 Thunderbird
 VLC Player
 FSLint
 Grsync
 Skype
  Adobe Reader
*Dropbox *(Get dropbox from link [http://db.tt/46gGLEm](http://db.tt/46gGLEm) - Your quota increases if you get referrals. My quota increases if you use this link to install Dropbox.)*

 **15. Replace Openoffice with Libreoffice:**

```
sudo apt-get purge "openoffice*.*"
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get install libreoffice
sudo apt-get install libreoffice-gnome
```[B]
16: Add the Canadian English spelling dictionary for LibreOffice:[/B]

Download and install the extension at:

[http://extensions.services.openoffice.org/en/node/1335](http://extensions.services.openoffice.org/en/node/1335)

**17. Extensions**:

I use the following Thunderbird Extensions, which are preserved if you keep your ./thunderbird directory when upgrading.

Custom Buttons 0.0.5.2
FireTray 0.2.8
Lightning 1.0b2
Zindus 0.8.29

I use the following Firefox Extensions: (also preserved if you keep ./mozilla when upgrading)

Adblock Plus 1.3.7

Find more extensions [here]("https://addons.mozilla.org").

**18: Add custom buttons in Thunderbird with scripts for 'Previous' & 'Next':** (the Thunderbird ones never work the way I like them to).

Right click on some open space in the toolbar. Add one button for 'Previous' and one for 'Next.' Then, right click the button you want to customise, click 'edit', and fill in the following information: 

    Name: Previous
    Image: file:///usr/share/icons/gnome/32x32/actions/back.png
    Code: /*CODE*/goDoCommand ("cmd_previousMsg");
    Initialization Code: /*Initialization Code*/
    
    On the 'Next' button, enter the following:

Name: Next
    Image: file:///usr/share/icons/gnome/32x32/actions/forward.png
    Code: /*CODE*/goDoCommand ("cmd_nextMsg"); 
    Initialization Code: /*Initialization Code*/

**19. Force Thunderbird to use 24 hour clock**:

```
sudo gedit /etc/default/locale
```Add the following line to the end of the file:
      
LC_TIME="en_DK.UTF-8"

Reboot.

I always used to work my way through the **[B][Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")**  [/B] for other good ideas, but I haven't this time on my Maverick install. I haven't tested DVD playback yet and will amend this list as necessary.

Good luck with your tweaks: post what works or doesn't work for your Thinkpad. I'm sure that many of these solutions aren't the most elegant, but they work for me. If you have a better solution for any of my above problems, I'd love to hear it. I also hope to post a totally command line version of these modifications where possible, to speed the process if I reinstall for any reason. Input appreciated!

Kolin

---

### Post by kolinab on 2011-02-09
[removed post and edited the original instead]

---

### Post by kolinab on 2011-02-15
My first and last intentional bump of this thread to raise its profile a bit.

K

---

### Post by HankB on 2011-02-15
> **kolinab said:**
> My first and last intentional bump of this thread to raise its profile a bit.

KI'll give it one more bump and say thanks for posting this!

Are you familiar with Thinkwiki? ([http://www.thinkwiki.org/wiki/Category:T60](http://www.thinkwiki.org/wiki/Category:T60)) I wonder if the info you posted here might be appropriate there (and be more likely to be found.)

thanks,
hank

---

### Post by tgalati4 on 2011-02-15
Or at least put a link to this thread on the T60 page.  I have a T43p and many of the tweaks also apply.

---

### Post by kolinab on 2011-02-15
Link added to [Thinkwiki t60 page]("http://www.thinkwiki.org/wiki/Category:T60"), as suggested. Cool, all these years and my first 'wiki edit' ever. Hope I did ok. :)

---

### Post by danielbu on 2011-05-29
My T60 (1953-D9U, souped with 2.5gb memory, 160gb hdd) won't work right following upgrade to 11.04 Natty Narwhal.

Everything seems fine, but when booting into the GUI, the keyboard doesn't work. Well, almost nothing works. The Fn keys work, or at least some of them. NumLk, brightness, thinklight. But the mouse buttons don't work, so I can't click inside the log-on password screen. The Shift+Ctrl combination works to change the keyboard language, too. But no focus change, no response to key combinations. 

Any ideas?

---

### Post by tgalati4 on 2011-05-30
OP seems happy with 10.10.

---

### Post by danielbu on 2011-06-11
I found that using aptitude in terminal to remove compiz and gnome do solved my problem.:D

Upgrading according to this thread is the next order of business. At the moment my middle button does nothing...

---

### Post by kolinab on 2011-10-12
OP (me) *was* happy with 10.10 but has since upgraded through 11.04 and now onto 11.10. I'll post a new tweaks thread once I get the kinks ironed out in my 11.10 install.

Here it is: [http://ubuntuforums.org/showthread.php?p=11334250#post11334250](http://ubuntuforums.org/showthread.php?p=11334250#post11334250)

---


---
title: "Getting Rid/Replacing Drum Sounds on Startup"
date: 2008-10-02
forum: General Help
---

### Post by patrickmollohan on 2008-10-02
All good.

---

### Post by Therion on 2008-10-02
But of course you can!  I typically replace the default sound scheme with the [Borealis sound scheme](http://gnome-look.org/content/show.php/%22Borealis%22+sound+theme?content=12584) but what ever you want to use you'll need to log in as root and change/replace them in **/usr/share/sounds**.

I'm not sure but I'm thinking Startup Manager might also allow you to simply turn off the startup sound if you'd prefer that.  Not 100% sure about that though.

Post back if you need more direction.

Edit:  Ugh... It's not Startup Manager.

Navigate to:  System/Preferences/Sound/Sound events/System Events

---

### Post by Rayaz on 2008-10-02
Disable drumroll from Login window in system prefrences.

---

### Post by thatDougore on 2008-10-02
You can also jump into System, Preferences, Sound; head over to the Sounds tab and pick & choose. The logon/out sounds are at the bottom. (UBUNTU 8.04 HH)

---

### Post by patrickmollohan on 2008-10-02
I understand how to change the sounds of when you log in and out, but I am talking about the drumroll thing when you get to the screen.  There is no drumroll options under sound.  I would like to know how to log on as root in a GUI, because I do not know how to replace or delete files from terminal (like what the codes are).  I tried to do the System-Administration-Login Screen Settings (or something like that) option configuration to allow this, but there is not Login Settings, only a "Logon Window".  How would I configure root as a GUI instead of terminal?

---

### Post by el-mar01 on 2008-10-02
Add this ppa to your software sources: [https://launchpad.net/~kwwii/+archive](https://launchpad.net/~kwwii/+archive)

Then install the ubuntu-sounds package.

---

### Post by brucenduane on 2008-10-02
To change or deactivate the login sounds on Ubuntu 8.04

Activate the Control Center:
Main Menu==>System==>Preferences==>Main Menu
   scroll down to System==>Administration
     Check the box for Control Center
        Close Window

Main Menu==>System==>Control Center
   Under the System section
      Click on Login Window
          Accessibilty tab
             Change the sound setting on Login Screen Ready


Hope this is helpful.

---

### Post by Aero-Z on 2008-10-03
Open System->Administration->Login Window. From there open Accesibility tab and untick the Login screen ready option.

---

### Post by patrickmollohan on 2008-10-03
Every time I click Login Window, it says it is starting in the taskbar.  Nothing pops up, then it disappears from the taskbar.

---

### Post by sayakb on 2008-10-03
If there is a problem with gksu, start it as sudo. At a terminal, type in:
```
sudo gdmsetup
```
And enter your password to invoke the login window prefs.

---


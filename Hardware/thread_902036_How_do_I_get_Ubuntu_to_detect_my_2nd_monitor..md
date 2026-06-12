---
title: "How do I get Ubuntu to detect my 2nd monitor."
date: 2008-08-26
forum: Hardware
---

### Post by coldstreak18 on 2008-08-26
Im running a HP laptop with an Nvidia card. i installed the drivers that it told me to download and its not working. My laptop monitor works great but my second monitor which is connected over VGA wont even be recognized how do i get it to see and use my second montior? I am brand new to linux so if i have to mess with config files youll have to be crystal clear i googled this a bit and i saw some code or whatnot.

---

### Post by IntuitiveNipple on 2008-08-27
I run Nvidia with dual monitors, so I'll be your host for this ride :)

I'll give you some commands to type in a terminal then describe how to use the Nvidia settings utility.

Open a terminal (**Applications > Accessories > Terminal**). Find out if you're using the Nvidia proprietary drivers:
```

$ dpkg-query -l 'nvidia-glx*' | grep '^ii'
ii  nvidia-glx-new 169.12+2.6.24.14-21.47 NVIDIA binary XFree86 4.x/X.Org 'new' driver

```
This confirms the Nvidia driver from Ubuntu's LRM (Linux Restricted Modules) package is installed.

Now to install the Nvidia X Server Settings manager:
```

sudo apt-get install nvidia-settings

```
There is now a graphical program installed. Run it from **Applications > System Tools > Nvidia X Server Settings**

In the left side-bar select **X Server Display Configuration**. Press the **Detect Displays** button.

At this point the graphical monitor position indicator should show two monitors. Select the new monitor. In the **Display** tab press the **Configure...** button.

To be able to have one large desktop spread across both monitors choose "TwinView". To run two independent screens each with their own settings and applications (no dragging windows between screens) choose "Separate X Screen". Press the **OK** button.

On the **X Screen** tab *for each monitor* adjust the layout and resolution of the screens to suit your preferences.

When you're happy with the settings press the **Save to X Configuration File** button. The resulting dialog-box will offer to save the settings to the system's X-windows configuration file. Usually **Merge with existing file** should be ticked. Press the **Save button**.

Close any running programs and log-out.

Now the acid test. X-windows will restart. If the settings you've chosen are good you'll get the log-in prompt on the primary monitor. After log-in both monitors should be active and usable.

---

### Post by coldstreak18 on 2008-08-27
I have it and when I go to do the next step and install those server settings it asks for a password but it wont let me type in the password whenever i hit a key on the keyboard the screen freezes for like a second then it goes back to just blinking. how do i type in my password?

---

### Post by IntuitiveNipple on 2008-08-27
When "Nvidia X Server Settings" is started the system should prompt for your password in order to run the program with elevated 'root' privileges, using gksudo.

From that point on there should be no more password prompts since the program is running as 'root'.

If there are, it sounds as if the permissions have been altered somehow in an unexpected way. If that is the case, I'm afraid it will be difficult to help you remotely.

---

### Post by kcsnare on 2008-08-28
I am having a similar difficulty in setting up my dual monitors.  I do all the steps, but when I click save I get this error:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

How can I fix this?

---

### Post by overdrank on 2008-08-28
> **kcsnare said:**
> I am having a similar difficulty in setting up my dual monitors.  I do all the steps, but when I click save I get this error:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

How can I fix this?

Are you root when using the nvidia settings? ```
gksu nvidia-settings
```

---

### Post by kcsnare on 2008-08-29
No, I was not.  I can now get settings to save but have a completely new problem.  I hope coldstreak doesn't mind me hiijacking his post but, I am trying to drive a 19 inch (primary) monitor and a 50 inch plasma (through a DVI -> HDMI cable).  I can get X server to drive dual 19 inch displays fine, but when I attempt the 19" and 50" combo, my 19" goes blank and the 50" never shows an image.  The system is still up and responsive, but my display kicks out on me, and the only way to fix it is to go into X server repair utility from boot.  Is there a fix for this?

---


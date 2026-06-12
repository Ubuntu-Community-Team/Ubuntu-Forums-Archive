---
title: "How to fix the Mini 10v Touchpad in Jaunty"
date: 2009-09-19
forum: Hardware
---

### Post by Tyrathect on 2009-09-19
This solution comes from the other thread on this and other forums. This turns out to be pretty easy because the code is already written, it's just not on the canonical distro.

The fix is easy, I just wrote it wordy so that everyone could follow it.

So, to fix it in ubuntu 9.04 (jaunty), do the following:

Use the ubuntu desktop menu system to open **System/Administration/Synaptic Package Manager**

in the package manager menu, select **Settings/Repositories **this will open a new dialog

First we're going tell the package manager where to find the new update.

select the **Third Party Software** tab, and click the **+Add** button in the lower left corner.

copy and paste the following into the **APT line** box:

[SIZE=1][B][FONT=Courier New]deb [http://ppa.launchpad.net/albertomilone/ppa/ubuntu](http://ppa.launchpad.net/albertomilone/ppa/ubuntu) jaunty main

[/FONT][/B][/SIZE]Then click **+Add Source** button to make the change.

Now click the **Updates** tab, and make sure **Pre-Release updates (jaunty-proposed)** is checked (I'm not sure if this is necessary, but better safe than sorry).

Click the** Close** button in the lower right corner of the settings dialog to close it.
 
Now we need to tell the system that the packages in the new repository are safe to download.  We do that by telling the system where it can download a security key.

open a terminal window from the desktop menu by selecting **Application/Accessories/Terminal**

In the terminal window, cut and paste the following (you can use ctrl-shift-v to paste into the terminal):

[FONT=Courier New][SIZE=1]**sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 99C0198F**[/SIZE][/FONT]

[FONT=Arial]press return to enter the command, and enter your password.  When the command completes, return to the synaptic package manager and press the blue **Reload** button in the upper left corner of the package manager.

Now the package manager is aware of the new code, we just have to tell it that we want to use the new code.

Cick on the **Search** button in the package manager, and type in the following:

[FONT=Courier New]**xorg-input-synaptic**[/FONT]
[/FONT]
Then click **Search**.

There should be one result, **xserver-xorg-input-synaptics **and under latest version it should say something like **0.99.3-2ubuntu4netbook1**

right click that line (or left click the green check box on the left side) and choose **Mark for upgrade**.

A new dialog will come up, click the **Mark** button.

After the dialog goes away, click the **Apply** button.

Once the installation completes, there's a few last things we should do.

We want to make sure that you don't accidentally get any other updates from that repository, so we're going to stop package manager from looking there.

Open up the repositories dialog again with **Settings/Repositories** from the package manager menu.

Choose the **Third-Party-Software** tab and uncheck the line with **ppa.launchpad.net** in it.

Now go to the **Updates** tab, and uncheck** pre-released updates**

close the settings dialog.

Now click the **Reload** button again so that your local files are up to date.

close the package manager

Now reboot and (hopefully) your trackpad will be working!

good luck.

---

### Post by thenickster on 2009-09-21
Spot on walkthrough!

Just tried it on my Mini 10v and, although I use an external mouse most of the time, it's good to have the trackpad working properly.

Cheers.

---

### Post by plopper2 on 2009-09-23
[FONT=Times New Roman][SIZE=3]When typing in[/SIZE][/FONT][FONT=Times New Roman][SIZE=3] 
[/SIZE][/FONT][FONT=Courier New][SIZE=1][B][FONT=System][SIZE=2]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 99C0198F[/SIZE][/FONT]
[/B][FONT=Verdana][SIZE=3][COLOR=black][FONT=Times New Roman]in the terminal I am getting an error

"gpg keyserver timed out
"gpg: keyserver receive failed: keyserver error" 

I am on a a wireless don't know if that would make any difference. Thanks for the help.
[/FONT]

[/COLOR][/SIZE][/FONT][/SIZE][/FONT]

---

### Post by plopper2 on 2009-09-23
Tried it again and it connected. Thanks again touchpad works awesome. :)

---

### Post by franklin_m on 2009-09-26
I just did it as well...and it works awesome! Thanks.

Frank

---

### Post by thebleublurr on 2009-10-06
This is an amazing fix. I am wondering whether there is a way to do this for Windows 7, as I am dual-booting and would love this functionality on my other OS! Please reply.

---

### Post by thebleublurr on 2009-10-06
I double posted and can't delete this, sorry.

---

### Post by mechanic on 2009-10-26
So does this add a .fdi file to the /etc/hal/fdi/policy/ directory or what? If so please post it! I take it it doesn't tinker with the xorg.conf file!!

---

### Post by JayUK20 on 2010-12-03
is there a way to make this work because i cannot see an upgrade option for xserver-xorg-input-synaptic

---

### Post by jsiret on 2010-12-26
Hello,

Should this also work on 10.04, trying to keep this clean.

Regards

---

### Post by anilakar on 2011-12-02
Apologies for bumping an old thread, but this is still the top result in Google if you search for "ubuntu disable touchpad bottom edge". The PPAs mentioned earlier only have packages up to Lucid, and as of writing this, Oneiric is the latest release of Ubuntu. The Mini 10v might not be able to run Unity, but there are dozens of other laptops out there whose mouse buttons have been embedded into the touchpad. The synaptics pad on my Lenovo E325 is rather horrible example of this.

Without installing the patched driver, it is possible to disable the bottom edge by typing the following in the console:

```
synclient AreaBottomEdge=4500
```

However, resting one's finger on the edge area disables the touchpad movement altogether, and it's impossible to cover large areas by tap-dragging. Alternatively it is possible to cheat by pressing the button with something non-capacitive such as a plastic ballpoint pen. 

Is there a working solution or are people forced to carry external mice with their netbooks?

---


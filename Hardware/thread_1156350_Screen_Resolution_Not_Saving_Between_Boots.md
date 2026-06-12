---
title: "Screen Resolution Not Saving Between Boots"
date: 2009-05-11
forum: Hardware
---

### Post by Ceiling Fan Man on 2009-05-11
The screen resolution I like to use is 1280x960 @ 85Hz. This option is not available in "System > Preferences > Display," so I use "System > Administration > NVIDIA X Server Settings" to get it.

  If I open it via Terminal...:
```
sudo nvidia-settings
```

 ...and set the screen resolution how I want it and Apply it, when I click "Save to X Configuration File" I get this from the error from nvidia-settings GUI:
> Failed to parse existing X config file '/etc/X11/xorg.conf'!

Followed by this error in Terminal:
> PARSE ERROR:  Parse error on line 34 of section Module in file /etc/X11/xorg.conf.
"Disable" is not a valid keyword in this section.

Segmentation fault

  Currently I have to boot then go to nvidia-settings and apply my resolution every single time I boot.

  **What can I do to get my Ubuntu (Jaunty) to boot into 1280x960 @ 85Hz?**

---

### Post by Ceiling Fan Man on 2009-05-11
My initial searches didn't come up with any topics, but while I was just browsing I found one that could have answered my question before I asked it. Here is a post I found that was most helpful:
> **ajayrockrock said:**
> How I fixed it:

1)  open a terminal
2)  sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2)  sudo touch /etc/X11/xorg.conf  
3)  sudo nvidia-settings
4)  hit "save configuration"

with the empty xorg.conf, nvidia-settings should properly save the file.

This did not work. I still got the failed to parse error... But it did inspire my working solution. The steps I took were as follows:

1)  open a terminal
2)  sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
3)  sudo nvidia-settings
    [Attempt to save, clicked Preview, copied the contents to a temporary TXT file for safe keeping during the procedure, close nvidia-settings]
4)  sudo gedit /etc/X11/xorg.conf
    [Paste all contents from the preview and save]

These steps worked great. :)

---

### Post by Barefootpanda on 2009-07-03
Instead of doing a sudo nvidia-settings you should be able to do
sudo su
nvidia-settings


This will actually run as root not a sudoer

---

### Post by merlinus on 2009-07-03
Since it is a graphical display, this is even better:

```
gksu nvidia-settings
```

---


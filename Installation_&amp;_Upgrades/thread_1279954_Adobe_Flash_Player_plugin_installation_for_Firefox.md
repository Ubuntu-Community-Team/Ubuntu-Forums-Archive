---
title: "Adobe Flash Player plugin installation for Firefox 3.5 fails"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by grkor on 2009-10-01
Installed (upgraded to0 Firefox 3.5 in Ubuntu. Fixed www connectivity problem (using help from this forum). However, Firefox asks for Adobe Flash Player installation (cannot watch cartain web pages videos without it). Installation fails each ti,me software is downloaded. How can Flash Video pluginbe added/installed to Forefox 3.5 in Ubuntu?  Pls help if you can.

---

### Post by dennisofnewport on 2009-10-01
I need the same kind of help. It has taken me four days to install firefox 3.5 hoping it would take care of flash problem. still unable to play flash even if I download the file and try to play the swf file I get "error occurred" GStreamer encountered a general support library error" sure wish it wasn't so complicated 

Thanks for your help.

---

### Post by Myshalla on 2009-10-02
Similar issue.  Ubuntu 8.10...Firefox 3.0.14....New user.
Long story short.... have tried several different forum suggestions.  Have tried to start from scratch by uninstalling all codec's and flash plugins figuring I had gummed up the system with too many failed fixes.  Went to Adobe to start over with 
[B]Adobe Flash Player version 10.0.32.18
Linux [/B]

The installer throws an error that says ERROR: A later version is already installed.
What does later mean?  Older or Newer version?  

I have not done command line work since DOS/Windows 3.1  I have checked the Add/Remove list and all flash related software is unloaded.  I have rebooted and I am still getting this error.

Thanks for your time.
Myshalla

---

### Post by oldos2er on 2009-10-02
Assuming each of you is running 32-bit Ubuntu, you can open either Add/Remove or Synaptic Package Manager and install the package ubuntu-restricted-extras, which gives you Flash, Java, mp3 codecs, and more.

 You can do the same thing in a terminal by running this command: ```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

 If you have any version of flash installed other than Adobe, e.g. gnash or swfdec, you will need to uninstall them.

---

### Post by Myshalla on 2009-10-03
Thank you Ann. 
Uninstalled gnash and swf.  Installed U-R-extras.
closed FF, logged off, logged on, opened FF, found YouTube.
Still no joy.

Did try the terminal command you sent and it failed with an error about not having a PubKey.  Have run into that on other issues. Still looking for a thread to tell me where to get these updated PubKeys.

Thank you for your time
Myshalla

---


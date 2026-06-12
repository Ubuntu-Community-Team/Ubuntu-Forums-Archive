---
title: "need help with flash fix - sound is gone"
date: 2008-09-21
forum: General Help
---

### Post by HarmonicaGoldfish on 2008-09-21
Hi everyone,

I tried out 2 fixes for the issues I was having with my firefox 3 browser and flash crashing it.

This is the first one, from [http://ubuntuforums.org/showthread.php?t=895885](http://ubuntuforums.org/showthread.php?t=895885) :


> Originally Posted by mb_webguy View Post
If you are using Hardy, then it's well known that there are issues with Flash and PulseAudio. If you use the version in the repositories (which snowpine suggested you install with the command "sudo apt-get install flashplugin-nonfree"), then you may also have to install the package libflashsupport to resolve these conflicts.

However, the version available for Intrepid that is in the Hardy backports repository doesn't have these problems. Enable the backports repository by going to System->Administration->Software Sources, clicking on the Updates tab, and selecting "Unsupported updates (hardy-backports)". Then type the following in the terminal.

```

sudo apt-get remove flashplugin-nonfree libflashsupport
sudo apt-get update
sudo apt-get install flashplugin-nonfree

```
Also, if you're still having problems with your Flash plugin, make sure you don't have any of the other Flash plugins like Gnash installed. You can type "about : plugins" (without the spaces) in the Firefox address bar to see what plugins you have installed.


That resulted in choppy browser functionality and no sound for videos.

So then I tried this:
[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

Which resulted in better browser functionality but still no sound.

I contacted mb_webguy and he offered some suggestions, but none worked. So he suggested I post a new thread and here we are :)

In between the 2 different fixes, I had not uninstalled anything, so I was thinking that might be the issue. However mb_webguy thinks that the 2nd fix should have effectively uninstalled any previous versions of flash before it gave me the new one.

Please help! I need sound back for my videos!
Thanks!
Tracy

---

### Post by HarmonicaGoldfish on 2008-09-21
oh...and I had no sound issues with flash before I tried these fixes. I'll even deal with the intermittent crashing if I can get my sound back :(

---


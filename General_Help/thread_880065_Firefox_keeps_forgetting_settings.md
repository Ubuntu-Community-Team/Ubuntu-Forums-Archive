---
title: "Firefox keeps forgetting settings"
date: 2008-08-04
forum: General Help
---

### Post by Kotjze on 2008-08-04
This only just started happening about an hour ago. I opened Firefox, and all my settings were gone. The only things still there were my bookmarks and extensions, but the settings for the extensions were gone. Even after changing some of the settings, every time I reopen Firefox, the settings are gone again! For about 10 minutes, if I opened an .html file, the settings were back, but now it stopped doing that, and opening an .html file gives me a setting-less Firefox :s I also tried restarting the computer to see if that worked, but it didn't. Any thoughts? :confused:

---

### Post by estyles on 2008-08-04
The one thing I can think of is, check the permissions on your .mozilla folder and make sure you have read-write access to it.  And also, you know, make sure it's there...  Also, posting the output of "ls" in .mozilla (and .mozilla/firefox if it exists - I forget exactly how the directory structure is set up) might help.

---

### Post by Kotjze on 2008-08-04
Oh, wow... Since you mentioned permissions, I thought I'd try running firefox as root, and all my settings are there when I do that.

And the permissions on my .mozilla say that I have read/write access.

Also:
```
josh@hp-linux:~$ ls .mozilla/
extensions  firefox
josh@hp-linux:~$ ls .mozilla/firefox/
profiles.ini  vkuuxfit.default
```

---

### Post by estyles on 2008-08-04
hmm... try ```
sudo ls /root/.mozilla/firefox/
```

maybe all your firefox data is in root's home directory?  Not sure why that would be...  if so, then you should be able to copy everything over as root and then chown those files back over to yourself.

edit: I should note that I'm no expert, so this might not be that helpful - just thought I'd take a crack at what seemed like it might be the problem.

---

### Post by Kotjze on 2008-08-04
There isn't a .mozilla in /root/

---

### Post by estyles on 2008-08-04
When you said that you ran firefox as root, did you use "sudo firefox" or "gksudo firefox"?  I believe that gksudo uses root's profile, but sudo uses your own profile but with root permissions.  Assuming you used your own profile, it really seems like something is up with your permissions.  I would try right-clicking your ~/.mozilla folder and on the permissions tab, make sure they're set correctly and then hit the "Apply Permissions to Enclosed Files" button (same effect as using chmod with the --recursive option), and see if that helps.  

If not, then I have no idea what could be causing the problem.  It might have something to do with the profile.  Firefox creates a pseudo-random name for your profile and then names it, in your case, vkuuxfit.default.  If for some unknown reason, firefox created a new pseudo-random name for you, you'd think there would be two *.default files in the firefox directories.

If you haven't solved your problem yet, try posting the contents of your ~/.mozilla/firefox/profiles.ini file.

---

### Post by Kotjze on 2008-08-04
It doesn't matter anymore. Just to start over again, I uninstalled Firefox, moved the .mozilla/firefox/ to somewhere and reinstalled Firefox. Then I copied over the extension folder, and my bookmarks, and also copied cookies.sqlite and places.sqlite so I would have all my old cookies and my history. Now it's working fine, and it's like I never changed anything :P

---

### Post by Master Chief on 2008-08-04
Next time you run into profile troubles, please, don't reinstall Mozilla Firefox again but simply use a new profile okay.

Tip: Backing up your profile(s) from time to time can be such a joy!

---

### Post by cszikszoy on 2008-08-04
Why is it that everyone seems so adamantly against reinstalling firefox in Ubuntu?  I heard it was because it breaks something (yelp maybe?).  I recently completely removed firefox (with the -purge option even) and reinstalled and everything works fine...?

---

### Post by Kotjze on 2008-08-04
I don't see how reinstalling it would break anything.

---


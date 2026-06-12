---
title: "Skype install issue"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by h0rnguy on 2009-06-11
Hi all!  Newbie to the ubuntu world here.  I downloaded the package installer and ran it through GDebi, and got this error message.  Error: Wrong architecture 'i386'  Anyone else have this experience or suggestions?

---

### Post by x33a on 2009-06-11
which processor are you using?

---

### Post by Bucky Ball on 2009-06-11
Your best bet is to add the Medibuntu repository to your software sources, update, and then load Skype from Synaptics (it is in the Medibuntu repository).

[http://my.oltrans.org/en/ubuntu-faqs/41-customizing/82-adding-medibuntu-repository-and-installing-restricted-extras.html](http://my.oltrans.org/en/ubuntu-faqs/41-customizing/82-adding-medibuntu-repository-and-installing-restricted-extras.html)

Don't forget to load the keyring (step 2). When you install Skype from the repos, it will install the correct version for your machine this way.

---

### Post by h0rnguy on 2009-06-12
I'm running an AMD Phenom 9850 quad-core.  Forgive my noobishness, but I followed the directions and installed medibuntu...  how do I access it now?  through the terminal?  I've used the Synaptic paackage manager before, but I gather Synaptics is something different.

---

### Post by merlinus on 2009-06-12
If you added the medibuntu repository, then skype should show up in synaptic.

---

### Post by Bucky Ball on 2009-06-12
> **h0rnguy said:**
> I'm running an AMD Phenom 9850 quad-core.  Forgive my noobishness, but I followed the directions and installed medibuntu...  how do I access it now?  through the terminal?  I've used the Synaptic paackage manager before, but I gather Synaptics is something different.

Your machine asked you to update and you did so after you added the Medibuntu repository?

1/ If so, go to System->Administration->Synaptic Package Manager, and do a search for Skype. If you have added the repo successfully, you will find Skype. Click the box next to it on the left and 'mark for installation.' Hit 'Apply' in the top left and you should be good to go. Skype will appear under 'Internet' in your 'Applications' drop-down menu.

2/ If no, open System->Admin->Update manager and update. If you hit a lot of errors, you may have forgotten to add the Medibuntu keyring (go back to link and step 2), or could be some other error. If no errors, go to step 1/ in this post.

:)

---

### Post by x33a on 2009-06-12
+1 for bucky ball, or if you like the command line way, then
```
sudo aptitude install skype
```

---


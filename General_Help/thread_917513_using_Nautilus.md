---
title: "using Nautilus"
date: 2008-09-12
forum: General Help
---

### Post by deaste on 2008-09-12
I upgraded to 8.04 a while back and have been installing s/w as I've needed it. I have to say there are some features in this release that I find less than impressive.

There were no useful graphics tools after the default install, I had to futz with the Nvidia drivers to get that to work, plus a few other disappointing surprises.

One of the things I'm still struggling to understand is the Nautilus file browser. I **cannot copy** files with it, only move them. Why is this and should I look for a more useful browser for ubuntu?

---

### Post by mb_webguy on 2008-09-12
Why can you not copy files in Nautilus?

What kind of "graphics tools" are you looking for?

---

### Post by iaculallad on 2008-09-12
Cannot copy files with NAUTILUS? Huh, had you even tried copying and pasting files yourself in Nautilus? Sorry to disappoint you but it had been working for me since I used Ubuntu.

As for the "useful graphic tools", what exactly do you want to perform so we could give recomendations of these graphic tools?

---

### Post by deaste on 2008-09-16
Nautilus is what the help button tells me I'm using. I've used Nautilus with other linux brands, like Knoppix, say, and a few others, which does have copy and paste, as I expect. I can recall copying and pasting with Nautilus several times.

The one I have on ubuntu 8.04 that was installed for me: v 2.22.3; does not have a paste option in the context menu, it does have a copy option but this doesn't seem to be useable (it does nothing obvious - if it copies something, that's all it does, you can't **use** the copy wherever it is). What did I do wrong in the install?

---

### Post by mb_webguy on 2008-09-16
So you're saying that if you right-click on a file and select "Copy", then right-click in an empty area of the Nautilus window, you don't get a "Paste" option, and if you right-click on a folder, you don't get a "Paste into Folder" option?  You won't get a "Paste" option if you're right-clicking on an invalid location to paste, such as a file.

---

### Post by deaste on 2008-09-20
> you're saying that if you right-click on a file and select "Copy", then right-click in an empty area of the Nautilus window, you don't get a "Paste" option, and if you right-click on a folder, you don't get a "Paste into Folder" option?Yes, that's exactly what happens - there is never a "paste" option available, whereas booting a live-cd, like gentoo or a live ubuntu cd, there is a paste option available.

I have absolutley zero idea why the installed OS won't let me paste files with nautilus. I can't install another filemanager either (selecting any other file manager in synaptic works, but the install doesn't)
 I consistently get "mlocate error" ??

This has me stumped.

P.S. I've been using Unix/linux for about 20 years. I know how to copy and paste files, or I'm quite sure I'm not trying to paste to a nonexistent or invalid location. If I select a file with a right mouse click, there's a "copy" option.

 If I copy the file, right click ON THE SAME FOLDER, there is no paste option in the context menu, this install has never shown that option - but WHY NOT?? Does anyone have a suggestion?

---

### Post by mb_webguy on 2008-09-20
I'm also somewhat at a loss.

After looking around a bit, I found one possibility that might be related to your problem...  Do you have DDM (Desktop Data Manager) installed?  Apparently it can cause problems with Nautilus.

The only other thing I can think of is that something has gone horribly wrong with your installation.  If you're having problems installing software, then you have more going on than a simple lack of copy/paste functionality in Nautilus.  You might want to consider reinstalling...

---

### Post by deaste on 2008-10-03
I gave up and reinstalled ubuntu.
Now there's another little problem, which is actually identical to a problem I had with ubuntu when I first installed it.

The problem: after the install, during which I saw no prompt to enter a password for the root user, I couldn't do any administrative things because that asks for the root password, which is unknown.

I thought doing a "sudo passwd root" from a console would fix this; I can now login as root on a console (yay!); however, from the desktop the same password is not accepted?? I can't do any desktop admin, because I need to supply the root password which is apparently still different to the password I use to login as root, terminal-session wise.

Now what? Why is ubuntu's password scheme so hard to deal with? Why doesn't the install prompt for a root password? Why did I have to do the "sudo passwd root" thing, and why doesn't that password work from the desktop??

---


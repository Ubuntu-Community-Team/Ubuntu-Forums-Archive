---
title: "Firefox 3 and Plugins"
date: 2008-07-24
forum: General Help
---

### Post by mykrob on 2008-07-24
Hey-

I was wondering if I did something wrong, or is this normal..
For Firefox 3, in order for plugins to work, i have to remove the directory /usr/lib/firefox-3/plugins  and create a symbolic link like so:

ln -s /usr/lib/mozilla/plugins /usr/lib/firefox-3/plugins


Today, firefox was updates, so I had to do this again, pointing the link to /usr/lib/firefox-3.0.1/plugins


I assume there is something wrong, surely they didn't expect average joe user to know how to create symlinks and such...

just looking for advice, because if I want to install this on someone else's computer, I don't want to have to go over and make a new symbolic link everytime Firefox is updated.

Thanks,
-myk

---

### Post by DirtDawg on 2008-07-24
I can't tell you what's wrong, but I can tell you that's not normal. I have Hardy installed on 2 separate computers and have not encountered anything like what you describe.

---

### Post by mykrob on 2008-07-24
hmmm. Firefox automatically shows the java plugins when i go to about:plugins.

Even though I have the multimedia plugins installed from debian-multimedia, they do not show up unless I make the symlink.

Let me ask this, what is the proper method for getting multimedia plugins for firefox 3 in Kubuntu? I am just used to adding the repository for debian-multimedia, and it may be that they are just installing to the "wrong" location.

Thanks,
-myk

---

### Post by mykrob on 2008-07-24
surely it isnt just me..

---

### Post by mykrob on 2008-07-25
bump

---

### Post by DirtDawg on 2008-07-25
I just reread your post. Are you saying you used debian-multimedia.org repositories? Debian .debs are created specifically for debian and are only sometimes compatible with Ubuntu.

I'm not sure what plugins you're specifically looking for, but there should be Ubuntu-specific ways to install most of them.

---


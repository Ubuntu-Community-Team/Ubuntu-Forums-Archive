---
title: "[SOLVED] HELP! User's $HOME/.dmrc file is being ignored"
date: 2008-08-15
forum: General Help
---

### Post by ragflan on 2008-08-15
Hi. I'm under Hardy Heron. I get this error everytime I login. 

**User's $HOME/.dmrc file is being ignored. This prevents the default session and launguage from being saved. File should owned by by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.** 

Stuff I did last night:
1.) sudo apt-get autoclean
2.) Backup the downloaded packages.
3.) sudo apt-get clean
4.) Backup my home directory to an external hard drive.

That's it. 

I found the .dmrc file in my Home folder and this is a screenshot of the Permissions tab. Please help. What does 644 permissions mean? Does it mean I have to check 'Execute'?

[IMG]http://ramipage.googlepages.com/Screenshot-.dmrcProperties.png[/IMG]

---

### Post by picpak on 2008-08-15
Try running

```
chmod 644 .dmrc
```

from a terminal. :)

---

### Post by ds[de] on 2008-08-15
Or to do it in the GUI:

Owner: [x] Read [x] Write [ ] Execute
Group: [x] Read [ ] Write [ ] Execute
Other: [x] Read [ ] Write [ ] Execute

---

### Post by ragflan on 2008-08-15
After I ran that command, the file's Permissions changed to:

[IMG]http://ramipage.googlepages.com/Screenshot-.dmrcProperties-1.png[/IMG]

Do I need to check 'Execute' for the Owner (me)?

---

### Post by iaculallad on 2008-08-15
Or, in your terminal:

```
sudo chmod 644 ~/.dmrc
sudo chown your_username ~/.dmrc
sudo chmod 755 /home/your_username
sudo chown your_username /home/your_username
```

---

### Post by ragflan on 2008-08-15
Thank you thank you for the quick replies!

---


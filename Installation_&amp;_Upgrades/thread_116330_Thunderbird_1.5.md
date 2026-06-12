---
title: "Thunderbird 1.5"
date: 2006-01-12
forum: Installation &amp; Upgrades
---

### Post by FrancJP on 2006-01-12
Hi, this is my first post, so hello everyone.

I've been looking for instructions to install thunderbird 1.5 in breezy, but with no luck. Do i have to follow [this steps]("https://wiki.ubuntu.com/FirefoxNewVersion") like in FF 1.5??.

Thanks in advance

Franc

---

### Post by kaamos on 2006-01-12
1) If installed, remove mozilla-thunderbird with synaptic
2) Get the package from mozilla.com
3) Extract
4) Move extracted folder to /opt with
```
sudo mv **thunderbird_folder** /opt/
```
5) Make symbolic link to executable with
```
sudo ln -s /opt/**thunderbird_folder**/thunderbird /usr/local/bin
```
6) Install libstdc++5 with synaptic
7) Start thunderbird by typing "thunderbird" in a terminal. If it works, you can create a launcher for it with the menu editor.

Replace **thunderbird_folder** with the real name of the folder.

---

### Post by FrancJP on 2006-01-12
Follow your instructions and works!!, thanks, but i have to make a profile for the new version... how can i copy my old profile to the 1.5??

Thanks

---

### Post by kaamos on 2006-01-12
Glad to hear it worked.

You can try, but it probably won't be much of a success. Your old profile is at /home/username/.mozilla-thunderbird and the new one is at /home/username/.thunderbird

---

### Post by FrancJP on 2006-01-12
I've tried in terminal to make a
> sudo cp /home/user/.mozilla-thunderbird/ /opt/thunderbird/defaults/profile/
But it won't let me make the copy :( 

Any ideas??
Thanks in advance

---

### Post by FrancJP on 2006-01-12
Sorry, but now works with no problem
I made a sudo mv instead of sudo cp :???: .
And the new profile where as kaamos said (i think the profile were in /opt/thunderbird).

Thanks for the help

---

### Post by PuNGS on 2006-01-12
I'm new here too, so hi to all!

There's a way to install Thunderbird 1.5 and keep my already downloaded by Thunderbird 1.0.7 e-mails?

---

### Post by lisje on 2006-01-12
Normally your mail is kept in your homedirectory, in the folder .mozilla-thunderbird.
It will not be removed if you uninstall your thunderbird 1.0.7.

greets,
Lisje

---

### Post by aysiu on 2006-01-12
[QUOTE=lisje]Normally your mail is kept in your homedirectory, in the folder .mozilla-thunderbird.
It will not be removed if you uninstall your thunderbird 1.0.7.

greets,
Lisje[/QUOTE] Except that Ubuntu's 1.0.7 stores the mail in ~/.mozilla-thunderbird and Mozilla's 1.5 stores it in ~/.thunderbird...

---

### Post by ephman on 2006-01-13
stange, i followed your instructions word for word and thunderbird won't fire up?  i just don't get it.

thanks,
ephman

got it fixed... shazzam it just started to work...

---

### Post by PuNGS on 2006-01-13
It worked, thanks. I copied the e-mails from ~/.mozilla-thunderbird.

---


---
title: "Right-click menu to files/images, send to e-mail menu"
date: 2008-08-04
forum: General Help
---

### Post by SergeiFranco on 2008-08-04
I am not sure if it is the right sub-forum, moderators please move it to the right section if it is not.

Here is the deal:

I am sick of unable to sent e-mails with attachments so easily as you do on windows.

In Windows you do right click on bunch of files and there is option send to email recipient, which brings new mail message window of preferred (default) e-mail client, with attachments already attached. Also if the files happen to be images it gives option of resizing them (to 640x resolution).
Why it can't be so easy in KDE (as I mainly use KDE - I hate nautilus, and GNOME in general seems to me too stupified and inflexible)?

I know that is possible to create such menu entries in KDE, so how do I make one? What about invoking script to resize the images if the files happen to be the images? 

I prefer Thunderbird over Kmail, so this must work with Thunderbird (or work with any default e-mail to be more flexible).

Also perhaps I should create another thread regarding the file picker (file chooser) being too dumb (GNOME, or dumbed down KDE filepicker, if messded with filepicker.js/about:config).

I know this is not Mozilla forum...I might sing up there and post same thing.

The current filepciker for mozilla products ain't good for anything. For example, I want to upload certain pictures to some online auction, here what happens:

I click "browse..", it comes with a stupid GNOME (or dumbed down KDE) filepicker in some random tmp file, then I have to navigate to home folder/picture location, then I have to open konqueror and have a look at thumbnails to find out the filename of the picture I want to upload (as there is no bloody way to change the view in filepicker to show the either thumbnails or preview) and then select my picture, repeat same process 20 times (or how many pics I have).

Now to  this better, there are following options:
1) Make the GNOME filepicker same type as used in GIMP (with preview feature)- not optimal for KDE users
2) Force to use Konqueror file picker (that has option of thumbnail view) and maybe with preview feature enabled
3) Make custom file picker that is platform independand.

We have to do better than Windows.

Thanks.

Sergei.

P.S. I have made a post before about file picker issue and there are other people complaining about the problem, but that got nowhere.

---

### Post by pauper on 2008-08-05
[rant]Well, why don't YOU _do_ something about it? Besides, as far as I know
ubuntuforums.org is in no way affiliated with Gnome or KDE development.
You got it all backwards--wrong URL. How can you demand something without
providing anything in return. Have you no shame?[/rant]

Regarding right-click-menu, might want to try nautilus-actions package:

```
sudo apt-get install nautilus-actions
```

[http://www.grumz.net/?q=taxonomy/term/2/9](http://www.grumz.net/?q=taxonomy/term/2/9)

---

### Post by SergeiFranco on 2008-08-05
> **pauper said:**
> [rant]Well, why don't YOU _do_ something about it? Besides, as far as I know
ubuntuforums.org is in no way affiliated with Gnome or KDE development.
You got it all backwards--wrong URL. How can you demand something without
providing anything in return. Have you no shame?[/rant]

Regarding right-click-menu, might want to try nautilus-actions package:

```
sudo apt-get install nautilus-actions
```

[http://www.grumz.net/?q=taxonomy/term/2/9](http://www.grumz.net/?q=taxonomy/term/2/9)

Well, I want to do something hence I ask how to do it in KDE.
If it is matter of script, yeah I can do.
But if it is more, well I ain't a programmer you know...
Nautilus is... well konqueror is a lot better.
I use KDE as it is a lot more flexible.

---

### Post by Sergio Jorás on 2008-11-16
Guys,
 I use Fedora but the tip below should work in Ubuntu too (as far as I know, you just have to figure out the right place to put the file). In Fedora, I created a file named email.desktop in /usr/share/apps/konqueror/servicemenus with the following lines:

[Desktop Entry]
Actions=Email
Encoding=UTF-8
ServiceTypes=all/all

[Desktop Action Email]
Name=Send file(s) with Thunderbird
Exec=thunderbird -P guest -compose "attachment=file://%U"
Icon=thunderbird

Note that the parameter "-P guest" is needed by TB (I use 2.0.0.14) in order to allow a new window to be openned while it's already running.
I hope this solves your problem!

Cheers,
Sergio.

---

### Post by space_agent on 2009-10-31
Hello,

I am using Kubuntu Karmic 9.10 and Kmail. I put the following in a file called email.desktop in the folder /home/user/.kde/share/kde4/services


[Desktop Entry]
Type=Service
Icon=dolphin
ServiceTypes=KonqPopupMenu/Plugin,all/allfiles,inode/directory,inode/directory-locked


Actions=Send_to
X-KDE-menu=Email
X-KDE-Priority=TopLevel

[Desktop Action Send_to]
Name=Send file with kmail
Exec=kmail --attach %U
Icon=kmail

Now with a right click I can send files by directly by right clicking in dolphin or konqueror. It would be nice if I could also send folders but I dont know how to do that.

greetings

---

### Post by Ganton on 2009-12-08
> **space_agent said:**
> Now with a right click I can send files by directly by right clicking in dolphin or konqueror. It would be nice if I could also send folders but I dont know how to do that.

Wow! Thanks! For sending files it works!!!!

---

### Post by Nikos.Alexandris on 2010-05-05
> **space_agent said:**
> Hello,

I am using Kubuntu Karmic 9.10 and Kmail. I put the following in a file called email.desktop in the folder /home/user/.kde/share/kde4/services


[Desktop Entry]
Type=Service
Icon=dolphin
ServiceTypes=KonqPopupMenu/Plugin,all/allfiles,inode/directory,inode/directory-locked


Actions=Send_to
X-KDE-menu=Email
X-KDE-Priority=TopLevel

[Desktop Action Send_to]
Name=Send file with kmail
Exec=kmail --attach %U
Icon=kmail

Now with a right click I can send files by directly by right clicking in dolphin or konqueror. It would be nice if I could also send folders but I dont know how to do that.

greetings

Really nice hack. Wonder why this isn't "official" in KDE yet?

---


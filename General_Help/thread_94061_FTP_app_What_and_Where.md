---
title: "FTP app? What and Where?"
date: 2005-11-23
forum: General Help
---

### Post by Optiker on 2005-11-23
I mentioned in another thread - but it's buried at the end and off topic for that thread - that I need to be able to FTP stuff, but didn't see an app in the original Kubuntu installation. I used Adept to install several - ftp, lftp and another that I don't recall the name of - wuftp or something like that - that was billed as an easy to use ftp program. Even after installing, I still do not see any of these in the "start button" (sorry for the Windows nomenclature - don't know what it's called in Linux) program listing.

Where would I find these (I suspect that they reside in some folder - /usr/bin? - but where is the launch icon/button?), or, which GUI ftp  would be the easiest for a person with my limited Linux experience? I think I now know how to use Adept to install new programs, but probably not if a recommended program is not in one of the default or added universe repositories.

Thanks!
Optiker

---

### Post by poekie on 2005-11-23
You could try searching for them with the find files and folders option? When I install something that doesn't turn up in the K-menu I use that and then create a menu-link using the edit K-Menu button you get when right-clicking the K. It's usually the file with the name of the program and a cogwheel as icon.

---

### Post by DoeRayMe on 2005-11-23
Use KBear for FTP

---

### Post by carney1979 on 2005-11-23
Kbear is in universe.

David

---

### Post by apokryphos on 2005-11-23
Konqueror is the default KDE FTP client, and a *very* good one at that; it's a KIOslave. In Konqueror, just [ftp://username@somedomain.com](ftp://username@somedomain.com)

---

### Post by metoo on 2005-11-24
Install gftp !
It will show up in the kde menu and uses the 'standard' screen: home left - remote right

Never felt home with kbear, might be just me. gftp is simple.

Downloading from a ftp server is possible with konqueror but maintaining a web side or anything like that is a charme with gftp.

---

### Post by wjp.reg on 2005-11-24
```
Install gftp !
```

:KS

---

### Post by nix4me on 2005-11-24
SecureFTP is the best FTP client I have found for Linux.  I use it everyday.  It's java based and it is very nice.

[http://www.glub.com/products/secureftp/](http://www.glub.com/products/secureftp/)

nix4me

---

### Post by Optiker on 2005-11-24
Thanks for the replies. I've installed kbear, but not tried it yet. I will also look into gftp, and also try Konqueror. I have already checked out the secureftp site, and it looks good, but probably overkill for me. I don't design and maintain web sites, but just occasionally need ftp to upload a file to my ISP server space to let somebody have access without having to e-mail, so perhaps Konqueror might be the best bet. However, I'll try tohe others as well and see what works best for me.

Thanks again for the suggestions.

Optiker

---

### Post by vh1 on 2005-11-25
[QUOTE=metoo]Downloading from a ftp server is possible with konqueror but maintaining a web side or anything like that is a charme with gftp.[/QUOTE]

actually, I find that adding the FTP (or whatever) site to your Remote locations the best way to maintain a remote website

---

### Post by gingermark on 2005-11-25
[QUOTE=Optiker]Where would I find these (I suspect that they reside in some folder - /usr/bin? - but where is the launch icon/button?)[/QUOTE]

Some programs won't add themselves the menu by default - you would need to do this manually (right click anywhere in the K-menu and click "edit menu").

However, check the "Debian" section of the K-menu, the entries are quite likely to be there, and then it is simply a case of drag & drop in the menu editor to get them where you want them.

---

### Post by Sham on 2005-11-25
[QUOTE=wjp.reg]```
Install gftp !
```

:KS[/QUOTE]

I third that! Very easy to use.

---

### Post by dc2447 on 2005-11-25
> **apokryphos]Konqueror is the default KDE FTP client, and a *very* good one at that said:**
> ftp://username@somedomain.com[/url] I'm not sure why people are ignoring you but it is the right answer

---

### Post by JPatrick on 2005-11-25
I like KFTPGrabber...

---

### Post by Drain on 2005-11-25
I'd like to voice my disappointment in all of you - here we are, in a **K**ubuntu thread and no one mentions [**Krusader**]("http://www.krusader.org/")? ;) (joking!)

Seriously, it's a very nice file-managing tool, very similar to gftp, and handles ftp, sftp, smb (Samba) connections flawlessly. It should be in the repositories.

---

### Post by angrykeyboarder on 2005-11-25
[quote=dc2447]I'm not sure why people are ignoring you but it is the right answer[/quote]


There is no "right answer". It's all about user preference.

Personally, for GUI-based ftp, I prefer gFTP to anything (including Konqueror or Nautilus).

---

### Post by goldenboy on 2005-11-26
I was wondering if any of the mentioned FTP-clients supports reconnects.

E.g. a site is restricted by the amount of simultaneously logged in users and you want the client to try to connect till the connection could be established.

I had the FTP-client problem myself some time ago, but was not able to find an adequate one for linux.

cheers

---

### Post by WirelessMike on 2005-11-30
The fireftp extension for firefox is very nice.  Very attractive and user-friendly

---


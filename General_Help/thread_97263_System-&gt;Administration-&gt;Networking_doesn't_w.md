---
title: "System-&gt;Administration-&gt;Networking doesn't work"
date: 2005-11-30
forum: General Help
---

### Post by lila on 2005-11-30
Hello, 
I'm trying to set up a dial up connection (yes, I believe I now have sorted out a modem that should work...), and I can't seem to get anything to enter the connection details into.  Searched various threads and the Wiki, and it all seems to point to the need to go into System->Administration->Networking, but when I try that, nothing opens.  It's like Networking is an icon on the Menu, but with nothing behind it.  Any ideas what I can do?
Thanks, Lila

---

### Post by sapo on 2005-11-30
What kind of dial up? You mean a 56k?

If you found a hardmodem in this time and age, grats, you are lucky.

And if thats the case.

Open up a terminal and type:

```
sudo apt-get install gnome-ppp
```

After installing it should be in the menu somewhere, just open it and configure your connection.

hope it helps :P

---

### Post by lila on 2005-12-01
[QUOTE=sapo]What kind of dial up? You mean a 56k?

If you found a hardmodem in this time and age, grats, you are lucky.

And if thats the case.

Open up a terminal and type:

```
sudo apt-get install gnome-ppp
```

After installing it should be in the menu somewhere, just open it and configure your connection.

hope it helps :P[/QUOTE]

Thanks, but no, I get "sudo: unable to lookup ubuntu via gethostbyname()".
It's the same message I get whatever i do in Terminal (not that i know what I'm doing there...)  I'm beginning to think it's an installation problem, so I'll re-install now.  Hopefully that will help.  Haven't entered anything since installing yet, so not a problem.
Cheers, and do let me know if you can think of anything else...  
By the way, found the hardmodem (PCI) in an old (8 years!)computer that was going to be dumped at work...  figured 8 years is probably safe for a fully hardware PCI modem... thank you Skor (Goddess of finding things and of Trashpicking)!
Lila

---

### Post by Specialsauce on 2005-12-01
thats the exact thing that happened to me (unable to lookup ubuntu via gethostbyname()) i had to reinstall to get rid of it, but ill bet there is a way to do it without a reinstall. whether its easier than a reinstall is questionable though.

---


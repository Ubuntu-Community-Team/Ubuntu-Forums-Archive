---
title: "[SOLVED] Can´t find skype"
date: 2008-09-29
forum: General Help
---

### Post by Freiberg on 2008-09-29
I have been assured that Skype is in the synaptic package manager, but I can´t find it.  I have even tried this, with no luck:

david@david-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
[sudo] password for david: 
--20:46:32--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[====================================>] 226           --.--K/s             

20:46:32 (14.03 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]

david@david-laptop:~$

---

### Post by ww711 on 2008-09-29
Probably better off going directly to the website for downloading and installing the .deb pkg....

---

### Post by anystupidname on 2008-09-29
> **Freiberg said:**
> I have been assured that Skype is in the synaptic package manager, but I can´t find it.  I have even tried this, with no luck:

david@david-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
[sudo] password for david: 
--20:46:32--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[====================================>] 226           --.--K/s             

20:46:32 (14.03 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]

david@david-laptop:~$

Well, Dave, I just (successfully) installed skype using exactly the method you describe. If, for whatever reason, that ISN'T working for you, I would suggest as ww711 has, using skype's DEB package provided here:
[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

> dpkg -i blah.deb

cheers

---

### Post by Freiberg on 2008-09-30
That worked.  Thank you.  :popcorn:

EDIT:  The reason I could not get it was that I have the wrong architecture.

---

### Post by lisati on 2008-09-30
> **Freiberg said:**
> That worked.  Thank you.  :popcorn:

That's good to hear.... Another success story. (I, too, downloaded the DEB package)

If you so choose, you can associate your skype ID with your forums profile (I have, you might notice the icon underneath many forum users' avatars) - you'll need to tell skype on your machine to allow others to see if you're online if you want it to show up in the forums.

EDIT: Just noticed I needed to tweak my skype status.....

---


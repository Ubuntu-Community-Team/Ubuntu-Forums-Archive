---
title: "lexmark s305 driver problem"
date: 2009-12-31
forum: Hardware
---

### Post by Arekun on 2009-12-31
hey, i just got a new Lexmark S305 and im having trouble getting it to connect to my computer. I went to the lexmark support website and followed all of the instructions there. it told me to download and install a driver. everything was going smoothly until i ran into the authentication page. it doesnt seem to recognise my administrative password.

i got the driver here: [http://support.lexmark.com/index?page=content&actp=DD_LIST&productCode=LEXMARK_IMPACT_S305&id=DR4255&os=UBUNTU_8.10&oslocale=en_US&segment=DOWNLOAD&userlocale=EN_US&locale=en](http://support.lexmark.com/index?page=content&actp=DD_LIST&productCode=LEXMARK_IMPACT_S305&id=DR4255&os=UBUNTU_8.10&oslocale=en_US&segment=DOWNLOAD&userlocale=EN_US&locale=en)

---

### Post by qujuntu on 2010-01-05
I am also having serious problems with Lexmark S305. I have chosen 64bit Ubuntu and they have only i386 support. I haven't found anything I could do. (Tried quite a lot of things though)

I've sent a question to their tech support; we'll see what they answer.


Edit: got it ok!
sudo dpkg --force-architecture -i dpkg -i installer_lpia.deb

---

### Post by steveneddy on 2010-02-16
> **qujuntu said:**
> I am also having serious problems with Lexmark S305. I have chosen 64bit Ubuntu and they have only i386 support. I haven't found anything I could do. (Tried quite a lot of things though)

I've sent a question to their tech support; we'll see what they answer.


Edit: got it ok!
sudo dpkg --force-architecture -i dpkg -i installer_lpia.deb

where did that .deb come from? I am not able to find it.

I also would like to install the Lexmark driver at GF's house and I am on 64 bit Ubuntu.

EDIT:

answer here:

[http://ubuntuforums.org/showthread.php?t=855415](http://ubuntuforums.org/showthread.php?t=855415)

Just need to change the name of the downloaded files to .sh from .download follow the instructions. worked perfectly for me. Can not scan but that's not an issue.

thanks for the scripts.

---

### Post by mazetas on 2011-05-02
hey, bit late but... 

i have the same printer, Lexmark s305, and till now I had managed to make it work. since i reinstalled my ubuntu though, I had to reinstall the printer too and guess what. on the website there is no more .deb driver anymore. it seems that lexmark supports just fedora and suse versions now. am I doing sth wrong or the company just wants nothing to do with the Debian family anymore?

could someone please upload the old driver somewhere?

Cheers

EDIT:

I must cancel my question. the site that i was looking for was the greek one. in .com it still exists.

Cheers double

---

### Post by hislordship on 2011-05-18
> **Arekun said:**
> hey, i just got a new Lexmark S305 and im having trouble getting it to connect to my computer. I went to the lexmark support website and followed all of the instructions there. it told me to download and install a driver. everything was going smoothly until i ran into the authentication page. it doesnt seem to recognise my administrative password.

i got the driver here: [http://support.lexmark.com/index?page=content&actp=DD_LIST&productCode=LEXMARK_IMPACT_S305&id=DR4255&os=UBUNTU_8.10&oslocale=en_US&segment=DOWNLOAD&userlocale=EN_US&locale=en](http://support.lexmark.com/index?page=content&actp=DD_LIST&productCode=LEXMARK_IMPACT_S305&id=DR4255&os=UBUNTU_8.10&oslocale=en_US&segment=DOWNLOAD&userlocale=EN_US&locale=en)


Hi mate - did you ever get an answer as to how to get it to recognize the password?

---


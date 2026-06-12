---
title: "Can't read Mac email attachments (binhex prob)"
date: 2008-07-11
forum: General Help
---

### Post by grw on 2008-07-11
Hi,
I have friends with Apple Macs and when they send me emails with attachments, I am unable to read them. 

This is what I get when opening a Word doc with Openoffice:
First, I am asked to select a character set in an ASCII Filter OPtions dialogue. (I tried UTF-8.) The file then opens and I am confronted with this:

(This file must be converted with BinHex 4.0)
:'9*PF'pbG#"dEb",5&-J5R9XH5!`1#jNEf-!9cK#6Ne69d3!N!5U!*!&#Tl3ca(
JSE%Di3#3%$i!!`$qr`N!"J#3#`%!N!03!*!)%!!!8J#3!`%!N!2qrj!$!*!%6`#
3!rq3rrq3XHbP`3#,B3N%!!$`%Vm!N!8"%3!"!!%!"J!!#3m!!!i!DQ*UBM($-F-
!N")*""B!-"i!!&ZK!!"ES3!!#3N!N"lrr`m!N!Rrr`m!N!Rrr`m!N"')!*!&M!%
!N!D-!3!!M!%!N!D-!3#3"S`"!*!'M!%!N!D-!3!!&!#3#m)"!*!'4J3!N!C'"!#

Similar problem with .jpg. Jpg files come with a message saying: Macintosh BinHex-encoded file attachment. 
I can't open them. I get this message:
Error interpreting JPEG image file (Not a JPEG file: starts with 0x28 0x54)

I tried installing libconvert-uulib-perl with Synaptic. No luck.

Can anyone help?

---

### Post by brian_p on 2008-07-11
> **grw said:**
> 
I tried installing libconvert-uulib-perl with Synaptic. No luck.

Can anyone help?

I've never used them but

```
apt-cache search binhex
```

throws up uudeview and xdeview.

---

### Post by grw on 2008-07-12
I found a website to decode Binhex. 

[http://www.webutils.pl/BinHex](http://www.webutils.pl/BinHex)

But how do I set it up so that when attachments arrive, I can just click on them and they open. Windows handled binhex encoding fine. Can't Ubuntu? (Installing uudeview and xdeview doesn't seem to help in this respect.)

Thanks

---

### Post by brian_p on 2008-07-12
> **grw said:**
> I found a website to decode Binhex. 

[http://www.webutils.pl/BinHex](http://www.webutils.pl/BinHex)

But how do I set it up so that when attachments arrive, I can just click on them and they open. Windows handled binhex encoding fine. Can't Ubuntu? (Installing uudeview and xdeview doesn't seem to help in this respect.)

uudeview has decoded the two or three files I gave it.

```
uudeview <filename>

```

and press the 'd' key.

The problem came after that because they have been archived with stuffit and there is no native Linux application to deal with this proprietary format.

---

### Post by grw on 2008-07-12
Thanks Brian.

---

### Post by brian_p on 2008-07-14
> **grw said:**
> Hi,
I have friends with Apple Macs and when they send me emails with attachments, I am unable to read them.

Someone with a similar problem to yours came up with a solution.

[http://ubuntuforums.org/showthread.php?t=859331](http://ubuntuforums.org/showthread.php?t=859331)

---


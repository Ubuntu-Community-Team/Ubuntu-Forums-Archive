---
title: "Help with command lines"
date: 2008-07-13
forum: General Help
---

### Post by RyanfromtheShire on 2008-07-13
So I'm using an iso compression program, for my PSP. Now it's fine, until I try and enter the directory the iso is in. It's on my desktop. So this is what I input:

```

ryan@ryan:~$ ciso
Compressed ISO9660 converter Ver.1.01 by BOOSTER
Usage: ciso level infile outfile
  level: 1-9 compress ISO to CSO (1=fast/large - 9=small/slow
         0   decompress CSO to ISO
ryan@ryan:~$ ciso 9 /desktop/ss.iso /desktop/ss.cso
Compressed ISO9660 converter Ver.1.01 by BOOSTER
Can't open /desktop/ss.iso
ryan@ryan:~$

```

I need to know if I'm putting the directory in correctly or not.

Thanks.

---

### Post by sisco311 on 2008-07-13
```
ciso 9 ~/Desktop/ss.iso ~/Desktop/ss.cso
```

---

### Post by RyanfromtheShire on 2008-07-13
For some reason, I'm still getting this:

ryan@ryan:~$ ciso 9 ~/Desktop/ss.iso ~/Desktop/ss.cso
Compressed ISO9660 converter Ver.1.01 by BOOSTER
Can't open /home/ryan/Desktop/ss.iso
ryan@ryan:~$

---

### Post by WRDN on 2008-07-13
I believe that error message is appearing because, you are currently in your home directory, and from there, you should not use the command "~/Desktop".
Try first changing to another directory. For example, "cd /", and run the command again.

Alternatively, it may be possible to first change to the Desktop by typing "cd Desktop" when the terminal opens, then using the command:

```
ciso 9 ss.iso ss.sco
```

---

### Post by RyanfromtheShire on 2008-07-13
I just moved the file, and did it like this and it worked:

```

ryan@ryan:~$ ciso 9 ~/SS.iso ~/SS.cso

```

Good to know about the ~, though!

---

### Post by shawnic on 2010-09-07
I used:
```
shawn@shawn-desktop:~/PSP$ ciso 4 KHBBS.iso KHBBS.cso
```

but I still get an error:
```
Can't open KHBBS.iso
```

---

### Post by The Cog on 2010-09-07
Did you realise that the thread you just tacked onto is over 2 years old?

RyanfromtheShire's problem seems to have been not paying attention to upper/lower case. ss.iso did not exist, but SS.iso did. Upper/lower case are different in *nix. 

That might be your problem too. Check that the file really exists with the command 
```
ls -l KHBBS.iso
```

---

### Post by grikdog on 2011-03-23
ummm...

the default info is

ciso level infile outfile

that means normal Linux CLI applies.

Try this:

if your iso file is on the desktop, type "ciso 9 " (with two spaces, without quotes) in the terminal, then click and drag the file anywhere onto your terminal window.

the infile now appears quoted and fully qualified on your command line.  

add a space at the end and click and drag the iso file into the terminal window again,
then edit iso to cso

press return

---


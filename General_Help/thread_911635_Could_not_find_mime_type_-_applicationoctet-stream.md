---
title: "Could not find mime type - application/octet-stream"
date: 2008-09-05
forum: General Help
---

### Post by kooldino on 2008-09-05
So no matter what I do on my machine (generally when I try to launch programs and such), I get the following error:

```
Could not find mime type
application/octet-stream
```

It may have started right after I went into the System Settings->Default Apps->File Associations and added a new type under "application".

Why is this happening and how do I fix this?

:confused:

---

### Post by mc4man on 2008-09-05
try going to home dir. (show hidden files -> .kde/share/mimelnk/application and see if there is a file - octet-stream.desktop

You could open it (with kate ) and see if there is a line hidden=true and change it to hidden=false.

Or just delete the file itself and reboot

Ot: ever find a decent disconnect or eject command for ipod?

---

### Post by unutbu on 2008-09-05
Perhaps look in each of these 3 files: ~/.mime.types, ~/.mailcap, and /etc/mime.types.

You should have the line
```

application/octet-stream			bin
```
in /etc/mime.types.

Also search for the new mime type that you recently added. If its format is off it might prevent the rest of the file from being read properly, causing the error message that you see.

---

### Post by kooldino on 2008-09-05
> **mc4man said:**
> try going to home dir. (show hidden files -> .kde/share/mimelnk/application and see if there is a file - octet-stream.desktop

You could open it (with kate ) and see if there is a line hidden=true and change it to hidden=false.

It is indeed there with hidden=true.

What else is interesting is that in that folder, there is a file "mysql.desktop"

mysql is the application type that i added the file assocation for...

I just wanted to run this all by you before I tried your instructions.

Re: ipod eject - I haven't hooked my ipod up in a couple of weeks, so I haven't gotten the chance to try the new suggestions.

---

### Post by mc4man on 2008-09-05
I can't really advise on 'technical' aspect, especially w/kubuntu which sometimes drives me crazy.

More on the thought that the if an error says it can't find .., let it be found and see what happens.

You can always edit it back to current setting (or **delete it** and reboot or look in mysql.desktop for something amiss 

I would also ck. post 3

> chance to try the new suggestionsif you mean sudo eject that was just a workaround, I was curious is something 'proper' was around

---

### Post by kooldino on 2008-09-06
> **unutbu said:**
> Perhaps look in each of these 3 files: ~/.mime.types, ~/.mailcap, and /etc/mime.types.

You should have the line
```

application/octet-stream			bin
```
in /etc/mime.types.


I have this line in my /etc/mime.types

[QUOTE]Also search for the new mime type that you recently added. If its format is off it might prevent the rest of the file from being read properly, causing the error message that you see.

It doesn't exist in /etc/mime.types

---

### Post by editrix on 2008-09-06
I had this problem with Dapper and solved it by removing

/home/username/.kde/share/mimelnk/application/octet-stream.desktop

as per this post: [http://ubuntuforums.org/showthread.php?t=386553](http://ubuntuforums.org/showthread.php?t=386553)

---

### Post by kooldino on 2008-09-06
Well, I bit the bullet and deleted "/home/username/.kde/share/mimelnk/application/octet-stream.desktop".  Without even rebooting it started working already.

So now the question is - why does that happen?

---

### Post by JamzY on 2008-09-16
I can confirm the solution and likewise biting the bullet and the errors immediately stopped. 

The contents of course were a result of the user-defined new mime-type I defined to handle TNEF in Thunderbird.

---

### Post by kooldino on 2008-09-17
Dammit.  Why does that happen?

---

### Post by mc4man on 2008-09-17
I dumped my kubuntu for various reasons but i was always curious if changing to 'hidden=false' had any effect?

Or before adding a new mimetype, *adding* 'application/octet-stream' as a mimetype *first* (isn't by default 

I believe 'application/octet-stream' is used for 'unknown' or 'unrecognized' file types (ext.'s

---

### Post by kooldino on 2008-09-18
I'm not sure if it would let you define a mimetype with no file extension.

---

### Post by mc4man on 2008-09-19
> I'm not sure if it would let you define a mimetype with no file extension.
Actually what I meant was add octet-stream first before adding/defining any other mime types or  setting file associations  (see screen - ( *. )

That creates the octet-stream.desktop that you deleted except it has hidden=false.
After that when you add/define a new type you won't get the pop ups anymore (tested

---

### Post by Pastor_JW on 2009-03-16
> **kooldino said:**
> Well, I bit the bullet and deleted "/home/username/.kde/share/mimelnk/application/octet-stream.desktop".  Without even rebooting it started working already.

So now the question is - why does that happen?

I just had this happen in 8.04 Kubuntu and so renamed the octet-stream.desktop to xoctet-stream.desktop and everything is back working.  Has anyone found out WHY it happens?  My machine was working fine yesterday but had this problem when I booted today.  Because of you posts it was fixed in less than twenty minutes!  Thanks all!  :)

---

### Post by lordbux on 2009-04-29
to put it simply
it happpens because the system sees multipne file associates or 
finds 2 different data files claiming different programs for the same filetype.or ...it goes on  but the actual reson usualy is the abow ones.
just confused. just correct it when it happens ..it susualy human error ,be careful when editing the kcontrol settings and file preference...donot rush:guitar:

---


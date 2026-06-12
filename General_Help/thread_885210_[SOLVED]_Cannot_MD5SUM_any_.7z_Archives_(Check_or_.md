---
title: "[SOLVED] Cannot MD5SUM any .7z Archives (Check or Generate) - Any Ideas??"
date: 2008-08-09
forum: General Help
---

### Post by OzzyFrank on 2008-08-09
OK, a bit of weirdness here that I can't seem to shake: I can't check the MD5sums of **.7z** compressed archives, at least using the **md5sum** command. I was sitting here checking a bunch of downloads, then came to some VMware images compressed in .7z format, which I know to be fine (not only could they open fine, they decompressed without issue and I've been using the virtual machines in VMware just fine). Besides, it's not telling me the files aren't fine, but that they don't exist. I'm not a newb to this so have of course made sure filenames correspond, etc. All the ISOs and EXEs I've been checking via **md5sum** haven't returned this error (unless it was warranted), so it begs the question: Does **md5sum** have trouble with .7z files for some weird reason? Any way around this??

[COLOR="DarkRed"]: No such file or directory
: FAILED open or read
md5sum: WARNING: 1 of 1 listed file could not be read[/COLOR]

As I've said, the files not only exist, but are fine too. Even corrupted files usually get the error that it didn't pass the check, not that it doesn't exist. And so far every single .7z archive I have tried to check has given me this error. Any help would be appreciated. Cheers.

---

### Post by OzzyFrank on 2008-08-09
Here is another slightly different error; note the z in readz:

[COLOR="Indigo"]md5sum: md5sum.txt: No such file or directory
: No such file or directory.7z
: FAILED open or readz
md5sum: WARNING: 1 of 1 listed file could not be read[/COLOR]

While the checksum is obviously not the error, I've checked it against one generated for the archive with a Windows app, and they match. Also, in case you're wondering if it is a filename and/or path issue, I've typed the name of the checksum file, dragged it to the terminal (so the whole path is included and inside quotation marks) and everything else I could think of (which I don't have to do for anything else I am checking).

I thought it couldn't hurt to rename the .7z as an .iso and change the reference in the .md5 file, but still no go:

[B]: No such file or directory.iso
: FAILED open or readso
md5sum: WARNING: 1 of 1 listed file could not be read[/B]

Cheers.

---

### Post by Vivaldi Gloria on 2008-08-09
try with the -b flag.

---

### Post by OzzyFrank on 2008-08-09
Tried that already, even though I knew it would tell me:

**md5sum: the --binary and --text options are meaningless when verifying checksums[COLOR="Red"][/COLOR]**

I'll try anything though at this stage, hehe. The **md5sum** command is definitely one of those terminal programs that have replaced GUI apps in my case, and I use it to generate and check sums for whole DVDs of data. This is the first time it has failed me, but I can tell you so far it definitely has problems with .7z files, whether I try to trick **md5sum** by renaming them or not.

As for generating the checksum, it now works, as I was going to try it again and paste the weirdness it spat out (nonsensical characters all over the place). Checking them still doesn't work though.

---

### Post by Vivaldi Gloria on 2008-08-09
```
vivaldi@narval:~$ md5sum -b test.7z
e98559a9681da702eacaf3237d7268b4 *test.7z

```

It works for me.

---

### Post by Habbit on 2008-08-09
The error message looks weird: "no such file .7z". Are you sure you are properly escaping any spaces/weird chars in the file name? md5summing a .7z compressed file works fine for me:```
$ p7zip maxout.gnuplot
7-Zip (A) 4.57  Copyright (c) 1999-2007 Igor Pavlov  2007-12-06
p7zip Version 4.57 (locale=es_ES.UTF-8,Utf16=on,HugeFiles=on,1 CPU)

Scanning
Creating archive maxout.gnuplot.7z
Compressing  maxout.gnuplot
Everything is Ok

$ md5sum maxout.gnuplot.7z > md5
$ md5sum -c md5
maxout.gnuplot.7z: Checksum matches

```

EDIT: if you are _verifying_ checksums instead of generating them, look inside the sums file: maybe the file names got broken or something... It's the only thing I can think about right now

---

### Post by OzzyFrank on 2008-08-09
Hi guys. First off, I can generate (without -b) but still can't check them with the -c option and the .md5 file.

Secondly, I am serious when I say I am not a newb to this, so having the filenames not matching, or somehow "broken", just isn't even a factor.

Thirdly, I've not only tried renaming to single-word prefixes (none had spaces, though that usually doesn't matter, at least not when enclosed in quotation marks), but have even tried renaming the extension. Other ISOs and ZIPs get checked fine... try to trick md5sum and it knows better.

I'm stumped, but at least can rule out user error.

---

### Post by Vivaldi Gloria on 2008-08-09
Can you please copy and paste the md5sum command you are trying and its output.

---

### Post by OzzyFrank on 2008-08-09
[B][COLOR="DarkRed"]ozzman@ubuntu666:~/CD & DVD/VMware DVDs/DVD-1$ md5sum -c dreamlinux.md5
: No such file or directory.7z
: FAILED open or readz
md5sum: WARNING: 1 of 1 listed file could not be read[/COLOR][/B]

or

[COLOR="Purple"][B]ozzman@ubuntu666:~/CD & DVD/VMware DVDs/DVD-1$ md5sum -c '/home/ozzman/CD & DVD/VMware DVDs/DVD-1/dreamlinux.md5'
: No such file or directory.7z
: FAILED open or readz
md5sum: WARNING: 1 of 1 listed file could not be read[/B][/COLOR]

---

### Post by Vivaldi Gloria on 2008-08-09
How about 

```
ls -l
cat dreamlinux.md5
```

in that directory.

---

### Post by OzzyFrank on 2008-08-09
ozzman@ubuntu666:~/CD & DVD/VMware DVDs/DVD-1$ ls -l
t[B]otal 4553688
-rwxrwx--- 1 ozzman ozzman  418229743 2007-04-13 22:55 centos-5.0-i386-server.zip
-rwxrwx--- 1 ozzman ozzman  534423520 2008-02-16 17:39 Dreamlinux-2.2-MMGL.7z
-rwxrwx--- 1 ozzman ozzman        865 2008-02-16 20:11 Dreamlinux-2.2-MMGL.txt
-rw-r--r-- 1 ozzman ozzman         58 2008-08-10 12:52 dreamlinux.md5
-rwxrwx--- 1 ozzman ozzman        632 2008-03-05 15:42 FCMD5-sums.MD5
-rwxrwx--- 1 ozzman ozzman 1271434458 2008-02-18 01:20 Gentoo-2007.0.7z
-rw-r--r-- 1 ozzman ozzman        562 2008-03-23 18:18 md5sum.txt
-rwxrwx--- 1 ozzman ozzman  668282833 2008-02-17 05:42 Pardus-2007.2.7z
-rwxrwx--- 1 ozzman ozzman  658519941 2008-02-25 02:34 Sidux 2007-3 Gaia.7z
-rwxrwx--- 1 ozzman ozzman        553 2008-03-23 17:49 Usernames & Passwords.txt
-rwxrwx--- 1 ozzman ozzman  714465434 2008-02-19 10:16 Vector Linux 5.9.7z
-rwxrwx--- 1 ozzman ozzman  392995567 2008-02-17 12:41 Zenwalk5.7z[/B]
ozzman@ubuntu666:~/CD & DVD/VMware DVDs/DVD-1$ cat dreamlinux.md5
**74344b2da607402e596c335dbb84928b *Dreamlinux-2.2-MMGL.7z**
ozzman@ubuntu666:~/CD & DVD/VMware DVDs/DVD-1$

---

### Post by Mister.Vash on 2008-08-09
Maybe the md5 has a dos CR/LF in in?  Try copying and pasting the text into a brand new md5 file via gedit and see if that works

---

### Post by Vivaldi Gloria on 2008-08-09
Ozzy, there is something wrong there. You're right. But I don't think it has something to do with .7z files. I think there is something wrong with that particular file.

md5sum with .7z files work in my computer:

```
vivaldi@narval:~/CD & DVD$ ls
Dreamlinux-2.2-MMGL.7z

vivaldi@narval:~/CD & DVD$ md5sum Dreamlinux-2.2-MMGL.7z > dreamlinux.md5

vivaldi@narval:~/CD & DVD$ ls
Dreamlinux-2.2-MMGL.7z  dreamlinux.md5
 
vivaldi@narval:~/CD & DVD$ md5sum -c dreamlinux.md5
Dreamlinux-2.2-MMGL.7z: Checksum matches
```

---

### Post by OzzyFrank on 2008-08-10
I was going to reply that most of the time I actually create the .md5 files myself, as usually the hash is just supplied on the download page, but then realised the files in question I only just found the download page for the .md5 files (so in other words were in fact downloaded). I figured if the syntax was correct, all should be fine (if the syntax is incorrect, you are told so in the error message). Turns out creating a new file and pasting the checksum info as-is ends up in an .md5 file that actually works!

I should mention also that all the .7z archives are from [http://bagside.com/bagvapp/](http://bagside.com/bagvapp/), which I wouldn't have thought would make a difference, but seems it does (I haven't downloaded much in .7z format, and nothing that needed to have an .md5 file with it, but all the VMware images there are in that format).

So, it has to be this "dos CR/LF" thing, which I am hoping someone can explain. Except that Vivaldi Gloria seems to have the exact same files and the check worked (???!!!). Oh, and to Vivaldi Gloria: no, as I've tried to explain, the files themselves are fine... I could compare checksums just not check with **md5sum - c** and the downloaded .md5 file. And also a major important factor: tried it on about 10 different archives and all apparently did not exist (noting that the error message always complained of missing files, not incorrect checksums).

Weird, especially if others are using the same MD5s that I downloaded before posting this thread.

[COLOR="#000000"][Edit] OK, missed the obvious that Vivaldi Gloria was not in fact using the downloaded MD5 but generating one and then using that to check.[/COLOR]

---

### Post by Vivaldi Gloria on 2008-08-10
> Except that Vivaldi Gloria seems to have the exact same files and the check worked (???!!!). 

No, they are not the same files. I just named them the same. ;) Just to see if there is something wrong with the name.

> Oh, and to Vivaldi Gloria: no, as I've tried to explain, the files themselves are fine... I could compare checksums just not check with **md5sum - c** and the downloaded .md5 file. 

OK. I see.  

May be you should file a bug report.

---

### Post by Mister.Vash on 2008-08-10
Ozzy, I did a little testing


I created a md5 sum, put it in a file, and verified that it worked
~/Desktop$ cat md5-original
74d6fcbac8febed55254e93384b6970e *Connect-userguide_en.pdf

~/Desktop$ md5sum -c md5-original
Connect-userguide_en.pdf: OK



I then edited the file in the windows notepad program - the text is the same, I just hit backspace to change the formatting to the dos CR/LF
This did not work
~/Desktop$ cat md5-windows-notepad 
74d6fcbac8febed55254e93384b6970e *Connect-userguide_en.pdf
~/Desktop$ md5sum -c md5-windows-notepad 
: No such file or directoryn.pdf
: FAILED open or readpdf
md5sum: WARNING: 1 of 1 listed file could not be read

I then loaded the file in gedit, went to the last line, hit backspace and enter, and it worked
 ~/Desktop$ md5sum -c md5-nonworking-pasted-into-gedit.mp5
Connect-userguide_en.pdf: OK
vash@fullmetal:~/Desktop$ 



So basically, open the dreamlinux.md5 file in gedit, go to the last line, hit backspace until you get to the end of the first line, and then just hit enter and save - hopefully that should do it

---

### Post by OzzyFrank on 2008-08-10
OK, so the fault can be replicated, and has definitely to do with Windows encoding of text files. Don't know if that means it's not a bug or it is, but at least we know **the answer**:

**[COLOR="DarkOrchid"]If an .md5 file is formatted correctly, and the file it refers to exists, is in the same folder, and has exactly the same name as listed, but you still can't get it to give you an OK or FAILED but just complains the file doesn't exist, then it is a DOS/Windows vs Linux thing, which can be rectified by either creating a new text file and pasting the info into that, or going to the second line and hitting Backspace (shouldn't need to hit Enter) and saving the file.[/COLOR]**

Thanks for everyone's help. While I don't usually mark workarounds to possible or confirmed bugs as [SOLVED], I think this qualifies. Hopefully other people with similar issues find this thread.

(PS: Still can't recreate the one-off weird error where I tried to generate a checksum for one of the .7z archives which resulted in gibberish and weird characters for quite a few lines in the terminal, and also in the terminal's title bar!)

---

### Post by _crash_ on 2010-06-16
Well, learning Bash is on my list of things to do for sure, but if I may but in, here goes...

Hopefully not too late to perhaps shed some light on this issue.  But if I am wrong, please correct me.

First off, [[COLOR="Red"]I found this thread via Google[/COLOR]]("http://www.google.com/#hl=en&source=hp&q=md5sum%3A+WARNING%3A+1+of+1+listed+file+could+not+be+read&aq=f&aqi=&aql=&oq=&gs_rfai=C6ujJckYYTIfVFqX4Mdrq-ecKAAAAqgQFT9DzJBg&fp=3021c2f615c58").

Second off, I know nothing about VMware or images compressed in .7z format.  But I had the exact same problem as OzzyFrank.

My story:  I was trying to use md5sum -c to verify the integrity of an ISO I just downloaded:  openSUSE-11.2-GNOME-LiveCD-i686-iso.

In the following Bash session dumps, I have changed my User ID and CPU ID.  Everything else appears as it did in Bash.  

Does any of this sound familiar?



```
UserID@CPUID:~/Desktop/openSUSE-11.2-GNOME-LiveCD-i686-iso$ 
UserID@CPUID:~/Desktop/openSUSE-11.2-GNOME-LiveCD-i686-iso$ md5sum -c openSUSE-11.2-GNOME-LiveCD-i686.iso
md5sum: &#65533;&#65533;&#65533;z&#1464;&#65533;&#65533;zN&#65533;&#65533;= K&#65533;&#65533;&#65533;qS&#65533;: No such file or directory
&#65533;&#65533;&#65533;z&#1464;&#65533;&#65533;zN&#65533;&#65533;= K&#65533;&#65533;&#65533;qS&#65533;: FAILED open or read
md5sum: WARNING: 1 of 1 listed file could not be read
UserID@CPUID:~/Desktop/openSUSE-11.2-GNOME-LiveCD-i686-iso$ 

```



Notice my stupidity in the above.  I ran md5sum -c _against the ISO file_ and NOT against the text file containing the md5 hash, **_which is what I should have done_**!

By the way, said text file that contains the md5 hash is named "md5" on my computer.  And I copied the hash which was in said text file right off of what was published on the [openSUSE web site]("http://download.opensuse.org/distribution/11.2/iso/openSUSE-11.2-GNOME-LiveCD-i686.iso.md5").

Here is my correction:



```
UserID@CPUID:~/Desktop/openSUSE-11.2-GNOME-LiveCD-i686-iso$ 
UserID@CPUID:~/Desktop/openSUSE-11.2-GNOME-LiveCD-i686-iso$ md5sum -c md5
openSUSE-11.2-GNOME-LiveCD-i686.iso: OK
UserID@CPUID:~/Desktop/openSUSE-11.2-GNOME-LiveCD-i686-iso$ 

```


Which is what I was expecting to get in the first place.  I used [[COLOR="Red"]aria2c[/COLOR]]("http://aria2.sourceforge.net/") to download the ISO.  And I used the Metalinks link to download the ISO, etc..  So I was expecting a 100% perfect ISO.  (I left aria2c's defaults alone.  One of said defaults is to have the "check chunks" option turned on, which is supposed to automatically fix anything bad that happens as the ISO downloads, etc.).

I can't believe how stupid I was regarding this...

Live and learn I guess.

Will this same technique fix OzzyFrank's problem?

Please reply and let me know if I am correct about my suggestion.  I realized my mistake by reading this thread.  So even if my suggestion to OzzyFrank is wrong, I would like to thank you guys for helping me out!


And in return, I hope what I have said helps you guys out.  


crash

---

### Post by _crash_ on 2010-06-16
I just did this two more times in Bash:



```
~/Desktop/openSUSE-11.2-GNOME-LiveCD-i686-iso$ md5sum -c md5
```



And both times got the same result:



```
openSUSE-11.2-GNOME-LiveCD-i686.iso: OK
```



So for what I was up against, it seems to have solved my problem.  Just wanted to let you guys know that my results are re-creatable.



crash

---

### Post by OzzyFrank on 2010-06-16
The solution is actually highlighted in my last post, being a Windows formatting issue with the text files. I've come across this quite a few times since (with .isos etc, not just .7zs), but knew what to do. Seems many people create their checksums in Windows (I personally find it infinitely quicker and easier in Ubuntu).

---

### Post by OzzyFrank on 2010-06-16
PS: Just to clarify what that means, when you open a *usable* md5 file, ie one made in Linux, the end of the document is at the **end of that one line** (assuming here the checksum file is for verifying one file only, of course).

In the *unusable* ones, ie made in Windows, the **end of the document is actually on line 2**, not at the end of line 1, so with the cursor in line 2 hit Backspace, so the end of the document is now the end of line 1 (not the beginning of a blank line 2). Save the file and it will now work fine.

Like I said, I've had to do that quite a few times since, but at least the solution is quick and simple.

---

### Post by xbackslashx on 2010-12-18
Having today encountered the same problem, I found this topic/thread quite useful to ascertain the cause of the problem and solve it.

I did some testing and indeed the difference lies solely in the newline format Windows uses as opposed to Linux.

some command-line examples follow:
```

$ ls -l
total 3
-rwxrwxrwx. 1 paddy_amd paddy_amd 178 Dec 18 12:05 file_integrity_check.binary
-rwxrwxrwx. 1 paddy_amd paddy_amd  62 Dec 18 12:09 file_integrity_check.binary-CHECKSUM-linux
-rwxrwxrwx. 2 paddy_amd paddy_amd  63 Dec 18 12:17 file_integrity_check.binary-CHECKSUM-windows

$ md5sum -c file_integrity_check.binary-CHECKSUM-linux
file_integrity_check.binary: OK
$ md5sum -c file_integrity_check.binary-CHECKSUM-windows
: No such file or directoryk.binary
: FAILED open or readbinary
md5sum: WARNING: 1 of 1 listed file could not be read

$ hexdump -c file_integrity_check.binary-CHECKSUM-linux
0000000   a   e   5   f   3   a   a   8   8   a   d   3   a   c   0   b
0000010   2   0   e   8   b   7   9   8   b   e   3   2   c   e   c   d
0000020           f   i   l   e   _   i   n   t   e   g   r   i   t   y
0000030   _   c   h   e   c   k   .   b   i   n   a   r   y  \n        
000003e
$ hexdump -c file_integrity_check.binary-CHECKSUM-windows
0000000   a   e   5   f   3   a   a   8   8   a   d   3   a   c   0   b
0000010   2   0   e   8   b   7   9   8   b   e   3   2   c   e   c   d
0000020       *   f   i   l   e   _   i   n   t   e   g   r   i   t   y
0000030   _   c   h   e   c   k   .   b   i   n   a   r   y  \r  \n

```So there it is, plain as daylight.

The straightforward workaround to this would be as OzzyFrank indicated to just manually remove the newline Windows' notepad inserts.

However when need to generate and create many checksum files in quick succession this workaround probably becomes unworkable so it would be preferable to automate this task perhaps by way of scripting.

I wonder, is the \r\n newline a Windows built-in or can it be modified to work with just \n like Linux does?

Just wanted to add this information to solidify findings of previous posters in this thread.

---

### Post by OzzyFrank on 2010-12-18
You could install the **[COLOR="DarkRed"]tofrodos[/COLOR]** package, and use the **[COLOR="Blue"]fromdos[/COLOR]** command (more info, including the **[COLOR="Blue"]flip[/COLOR]** command: [http://ubuntugenius.wordpress.com/2010/10/26/how-to-convert-windowsdos-text-files-to-linuxunix-format/](http://ubuntugenius.wordpress.com/2010/10/26/how-to-convert-windowsdos-text-files-to-linuxunix-format/)). You would then simply use **[COLOR="Blue"]fromdos *.txt[/COLOR]** or **[COLOR="Blue"]fromdos *.md5[/COLOR]** or whatever to batch convert all the checksum files in that folder.

---


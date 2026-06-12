---
title: "[SOLVED] [8.10] xmltv issues"
date: 2008-11-05
forum: General Help
---

### Post by lovinglinux on 2008-11-05
I use Freeguide and OnTV applications on Hardy without problems, but on Intrepid they do not update the TV schedule from a xmltv file.

Anyone experiencing the same problem? Any idea how to fix this?

---

### Post by lovinglinux on 2008-11-09
OnTV is working now, so I guess Freeguide issue has something to do with java.

---

### Post by NoVista on 2008-11-14
OnTV ain't no Freeguide.

Freeguide does work on Intrepid, but not the one in the repository.
Go get freeguide-0.10.9-bin instead.

If it is hanging when you try to update the listings, do the following:
In your Home folder, make a file called ".freeguiderc"
Inside that file, add the line:
FREEGUIDE_OPTS=-Xmx512m

Save and close and re-start Freeguide.

---

### Post by lovinglinux on 2008-11-14
> **NoVista said:**
> OnTV ain't no Freeguide.

Freeguide does work on Intrepid, but not the one in the repository.
Go get freeguide-0.10.9-bin instead.

If it is hanging when you try to update the listings, do the following:
In your Home folder, make a file called ".freeguiderc"
Inside that file, add the line:
FREEGUIDE_OPTS=-Xmx512m

Save and close and re-start Freeguide.

Thank you. How do I install freeguide-0.10.9-bin? Just copy freeguide file to /usr/bin an the rest to /usr/share/freeguide?

---

### Post by NoVista on 2008-11-25
As an alternative, you can install the Debian sid (unstable) package: freeguide (0.10.9-1).
That Debian package works fine for me on 8.10 also.

[http://packages.debian.org/unstable/misc/freeguide](http://packages.debian.org/unstable/misc/freeguide)

---

### Post by lovinglinux on 2008-11-26
> **NoVista said:**
> As an alternative, you can install the Debian sid (unstable) package: freeguide (0.10.9-1).
That Debian package works fine for me on 8.10 also.

[http://packages.debian.org/unstable/misc/freeguide](http://packages.debian.org/unstable/misc/freeguide)

Thanks. Unfortunately, it still not working. The program loads, but instead of grabbing the *.ser files from the working folder (I created those in my machine), it keeps asking for the xmltv file. Then I import a xmltv file, but nothing happens despite the CPU usage going to the top and staying there.

---

### Post by NoVista on 2008-11-26
Have you tried a clean install of that debian file, with no importing of already created files by you,  after removing any trace of freeguide from before?

I don't import any xmltv file at setup, if I remember correctly, once the prog comes up, you have to tell it what grabber you use and then go from there. Once you give it your account info if needed for the grabber, then you hit the download listings, but not until then.

---

### Post by lovinglinux on 2008-11-26
> **NoVista said:**
> Have you tried a clean install of that debian file, with no importing of already created files by you,  after removing any trace of freeguide from before?

I don't import any xmltv file at setup, if I remember correctly, once the prog comes up, you have to tell it what grabber you use and then go from there. Once you give it your account info if needed for the grabber, then you hit the download listings, but not until then.

The problem is that we don't have a working grabber in my country, but we have an EPG provider that distribute the xmltv file for download. So I have to import it. It works fine on my desktop running 8.04 this way. If I put the list.xmltv in the freeguide working directory, the program will automatically convert it to *.ser files when starting, without prompting for download. This is not happening in the intrepid machine.

---

### Post by NoVista on 2008-11-27
I tried to import my old file also when I first installed Intrepid.
It didn't work for me either that way.

---

### Post by lovinglinux on 2008-11-27
I tried a fresh install. No joy.

I put the xmltv file in the working directory before opening the program for the first time and it converted it to *.ser files, but the schedule dos not show up.

Then tried to import and got the same result.

So, the xmltv file is recognized and converted, but the data is not displayed.

---

### Post by lovinglinux on 2008-12-02
I finally got the Debian package working, after deleting ~/.java/.userPrefs/org/freeguide-tv folder. This folder is not deleted when doing an apt purge and it seems to be the source of the problem.

---


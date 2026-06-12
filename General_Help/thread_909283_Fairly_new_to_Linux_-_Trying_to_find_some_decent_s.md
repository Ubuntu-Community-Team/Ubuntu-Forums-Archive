---
title: "Fairly new to Linux - Trying to find some decent stock trading tools or software"
date: 2008-09-03
forum: General Help
---

### Post by hoboholmes on 2008-09-03
I am fairly new to Linux but am getting the hang of it pretty easily. I am relatively computer savvy. I have an account with Scottrade that has a very nice platform but their Java applet doesn't work on Ubuntu no matter what I do. I have tried multiple things and it just won't work. I think it's Scottrade's applet that's the problem. I still want to keep my money in my Scottrade account but am wondering if there is any software or web based platforms that I can use that will give me streaming charts and other tools in real time. I don't even mind if I have to pay for it, but this is the only thing keeping me from switching completely over to Linux right now. I am so sick of windows and I really want to make the switch. Also, I don't want to use wine or anything similar to that. I want a dedicated Linux system with no need for windows software. I also would like to know what kind of a program I can use on Ubuntu that is similar to daemon tools in windows that I can use for mounting disc images. I would really appreciate it if someone can help. Thanks.

P.S. I am using the latest 64 bit version of Ubuntu but can switch to a 32 bit if I need to.

---

### Post by josephtmoran on 2008-12-05
were you ever able to resolve this situation with scottrade? i have the same issue.

---

### Post by mitso on 2008-12-05
Stick with UBUNTU ! I'm also new to UBUNTU and have a Scottrade account. You must install the JAVA applet in UBUNTU. I had to
reinstall UBUNTU this week. My first install was about a month ago.
I installed all of the scottrade stuff with the ubuntu Java applet.
and all worked fine including the streaming quotes.
I will have the scottrade stuff back on in the next day or so and
get back on with the procedure - I hope !

---

### Post by ncanna1 on 2008-12-05
As for the mounting disk images, you can do that simply from your command line.  First, make an empty directory in the /media directory.

```

sudo mkdir /media/iso1

```

Then, you can mount the iso using the mount command.

```

sudo mount -o loop iso9660 locationofisohere /media/iso1

```

You should then be able to access the images as if the cd were in a drive.

---

### Post by jheaton5 on 2008-12-05
> **ncanna1 said:**
> As for the mounting disk images, you can do that simply from your command line.  First, make an empty directory in the /media directory.

```

sudo mkdir /media/iso1

```

Then, you can mount the iso using the mount command.

```

sudo mount -o loop iso9660 locationofisohere /media/iso1

```

You should then be able to access the images as if the cd were in a drive.

Then, one could download the ubuntu live cd iso to the hd, mount the iso and install ubuntu without needing any cd.  I'm thinking about my Dell mini 9 which does not have a cd rom.  I know I can make a usb boot disk but I'm always looking for options.

---

### Post by mitso on 2008-12-06
I reinstalled scottrade and all worked fine except for the streaming quotes. I know just enough BASH to get me in trouble. I'm having a problem installing the java applet that's required to run the streaming quotes. I'll keep you informed. I thought I used the same
procedure, but I guess not.

---

### Post by mitso on 2008-12-08
After messing about with my (knowledge?)of BASH,
I decided to re-install. I'm using 8.04 in a separate computer. The installation went fine. The first thing I did after the installation was log on to scottrade and clicked on streaming quotes.
Next, ubuntu told me I needed a java applet and did I want it intalled. I clicked yes on all the buttons as it was being installed, and up popped streaming quotes. AS EASY AS THAT !!

As it turns out UBUNTU knows a bit more about UBUNTU than I do. But I'm learning.

I hope this helps.

---


---
title: "libltdl3 in 8.10"
date: 2008-11-11
forum: General Help
---

### Post by JoKo on 2008-11-11
Hi,

I am using a close sourced program which requires the shared library libltdl.so.3.

I think there was a libltdl3 package for that library, but I can't locate it in Ubuntu 8.10.

Is there any way to install this library?

---

### Post by razorxpress on 2008-11-22
Download from [http://packages.ubuntu.com/hardy/libltdl3](http://packages.ubuntu.com/hardy/libltdl3) and install on 8.10

---

### Post by JoKo on 2008-11-22
Nice idea.

I have done something else, though: I've created a symbolic link of libltdl.so.7 to libltdl.so.3. Luckily my closed sourced application worked!

---

### Post by techflat on 2008-12-10
> **JoKo said:**
> Nice idea.

I have done something else, though: I've created a symbolic link of libltdl.so.7 to libltdl.so.3. Luckily my closed sourced application worked!

Hey there JoKo

Sounds nice, how did you do that?

Cheers
techflat

---

### Post by techflat on 2008-12-10
Hi there,

I just installed libltdl3 so I could work with another package that needed it (if anybody needs to know, it's a package made by Avasys for my Epson Printer and Scanner).

I downloaded it from here:
[http://packages.debian.org/etch/i386/libltdl3/download](http://packages.debian.org/etch/i386/libltdl3/download)

And all the info for the package is here:
[http://packages.debian.org/etch/libltdl3](http://packages.debian.org/etch/libltdl3)


Cheers

**Edit**:
I can't install the package, apparently there is a conflict with pulse. It seems that this version is too old for pulse. I tried with the unstable version and I can install it, but, well.... its unstable so I don't think I am going to leave it installed. Here's the unstable version page from debian.org: [http://packages.debian.org/sid/libltdl3](http://packages.debian.org/sid/libltdl3)

---

### Post by JoKo on 2008-12-10
> **techflat said:**
> Hey there JoKo

Sounds nice, how did you do that?

Cheers
techflat

Hi,

It's really simple:

> cd /usr/lib
sudo ln -s libltdl.so.7 libltdl.so.3

---

### Post by techflat on 2008-12-10
> **JoKo said:**
> Hi,

It's really simple:

Thanks for your reply, I thought it was something like that that you did.

However, this method doesn't work for me, I'm guessing it's because I'm trying to install a .deb package and it looks in a database for installed packages or something, but I don't really know why this happens.

When I try to install my package with the package installer, I get the following error (after doing your method):
```
[COLOR="Red"]**Error: Dependency is not satisfiable: libltdl3**[/COLOR]
```

Did you use your method to install a .deb package? If so, how did you do it? Is there some additional step I'm missing?

Cheers

---

### Post by JoKo on 2008-12-11
Perhaps I wasn't clear...

Since I had the file **libltdl.so.7**, I thought it was obvious I had installed the **libltdl7** package.

You can install that package directly via apt-get, it's an Intrepid one and is located in Ubuntu mirrors (check [here]("http://packages.ubuntu.com/intrepid/libltdl7")).

After I installed the package, I've just linked the library like I said before.

---

### Post by techflat on 2008-12-13
> **JoKo said:**
> Perhaps I wasn't clear...

Since I had the file **libltdl.so.7**, I thought it was obvious I had installed the **libltdl7** package.

You can install that package directly via apt-get, it's an Intrepid one and is located in Ubuntu mirrors (check [here]("http://packages.ubuntu.com/intrepid/libltdl7")).

After I installed the package, I've just linked the library like I said before.

Well I already had libltdl7 installed, that's why I tried your method, but it did't work... That's why I was asking if you were using this method to install a .deb package or some other sort of program distribution style.

---

### Post by JoKo on 2008-12-13
What exactly didn't work?

The symbolic linking or the program depending on libltdl.so.3?

---

### Post by techflat on 2008-12-15
> **JoKo said:**
> What exactly didn't work?

The symbolic linking or the program depending on libltdl.so.3?

Well, the symbolic link worked OK, but I could not install the package I have because when I open the package installer there's this red bold message:
```
[COLOR="Red"]**Error: Dependency is not satisfiable: libltdl3**[/COLOR]
```

That's why I asked, did you install a .deb package with your solution or what did you install?

Cheers

---

### Post by JoKo on 2008-12-22
I see. No, I've just installed a binary program without any deb packaging at all.

---

### Post by bailout on 2009-01-03
> **razorxpress said:**
> Download from [http://packages.ubuntu.com/hardy/libltdl3](http://packages.ubuntu.com/hardy/libltdl3) and install on 8.10

How safe is it to install a hardy package in 8.10? I have just tried installing drivers for a scanner that need libltdl3 and have run into the same problem that the package isn't available in the intrepid repos.

---

### Post by bailout on 2009-01-03
I decided to try installing the hardy package and it seems to have worked without any problems.

---

### Post by nukeqler on 2009-05-21
See also the resolution of this thread:

[http://ubuntuforums.org/showthread.php?p=7323695](http://ubuntuforums.org/showthread.php?p=7323695)

---

### Post by trent_b on 2009-12-13
After researching pulseaudio I decided I could do without it.  I uninstalled it with synaptic and then installed libltdl.so.3 using the method described in this thread. 

I too needed it for an Avasys driver for an Epson printer.  Using the driver I've got it working over USB but so far not over the network.  Any suggestions.  I can see the printer and even send things to it but then it just does nothing.

Insidently I bought the printer to replace a Lexmark I bought before I got into GNU/Linux and I have written to Lexmark to let them know I'm giving away one of their printers because they don't support linux

---


---
title: "Problem with Remote X-forwarding in Intrepid"
date: 2008-11-06
forum: General Help
---

### Post by C-- on 2008-11-06
I have having issues when I try to open a GUI over ssh in Intrepid Ibex. I am currently using the nvidia 177 driver (I tried 173), though I used to use xgl to run my X server before it was removed from the repositories.

I can open a file in a text editor such as gedit and emacs, but the minute I press an alphanumeric key I get the following error:

X protocol error: BadAlloc (insufficient resources for operation) on protocol request 150

---

### Post by C-- on 2008-11-06
*bump*

---

### Post by ju2wheels on 2008-11-06
What command are you running?

I have the nvidia 177 graphics drivers as well and I can forward X over ssh without a problem, Ive even used it to remotely access Thunderbird and send emails.

---

### Post by C-- on 2008-11-07
I use ssh -X [username]@[hostname] to connect to a remote system. I then attempt to open a text file using a variety of programs, such as emacs and gedit. For example to edit the file "file.txt", I type "emacs file.txt". This opens a GUI for the respective program (i.e. the file is not opened in the terminal). When I try to modify the file (i.e. adding or deleting text), I get an error. With emacs, it's:

X protocol error: BadAlloc (insufficient resources for operation) on protocol request 150

With gedit, its:

The program 'gedit' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 1825 error_code 11 request_code 150 minor_code 16)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by C-- on 2008-11-08
*bump again*

---

### Post by C-- on 2008-12-02
It seems the problem was solved in a recent update (which update I do not know).

---

### Post by missfroguk on 2008-12-03
Lucky you! I have just downloaded the latest updates and my problem is persisting!

I'm having EXACTLY the same problem except that my error message is 

X protocol error: BadAlloc (insufficient resources for operation) on protocol request 148 (rather than 150). 

I installed Ubuntu last week and without the X server, I can't really use it.

Can anybody help?
Thanks

---

### Post by missfroguk on 2008-12-03
Actually, this only seems to happen with one of my ssh -X addresses. Another one works perfectly well. 

Any idea?

---

### Post by Nepherte on 2008-12-03
I thought you had to run an x server.

---

### Post by missfroguk on 2008-12-03
I'm new at Ubuntu (so maybe it's the wrong forum but I just continued a thread). when I typed the command ssh -X [username]@[address] and the X window opened, I assumed I didn't have anything else to do. 

Besides as I said, I don't get that problem when I log on to another server and open emacs.

---

### Post by missfroguk on 2008-12-16
Just in case it helps anybody in the future: the IT people in charge of the remote server I had problems accessing managed to track down what was wrong: the libxml in Solaris 9. Despite applying all the latest patches and upgrades it still didn't help. So they put a Solaris 10 box onto the network and it now works perfectly fine.

---

### Post by avongil on 2009-09-07
I'm having the same problem!  

This happens when I log onto a sun machine and try to run a gtk app..  For example gedit does not work.  this is running ubuntu 9.04

Now, here is the kicker.  Works perfectly fine on my eeebuntu 3.0 netbook.  should be almost the same OS right??

I log into the sun machine like this.
ssh -X -l username xxxx.njit.edu

Here are a few differences that I can see:

xclock and eyes both run on eeebuntu and ubuntu, but on eeebuntu it displays "xclock (on compname.njit.edu)"

on my ubuntu machine, it displays "xclock"


gedit and proe run find on eeebuntu machine, but fail to start on the ubuntu machine.  i don't understand, its virtually the same thing!



:confused:

---

### Post by avongil on 2009-09-10
Anyone?  Please...

---


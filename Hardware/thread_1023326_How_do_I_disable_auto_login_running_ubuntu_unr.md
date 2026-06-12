---
title: "How do I disable auto login running ubuntu unr"
date: 2008-12-27
forum: Hardware
---

### Post by mrkwrnch on 2008-12-27
just installed notebook remix on an hp mini.  works great right out of the box.  My only problem is the it logs me in with out a password entry. don't have any idea where to go as the system> administration > login window does not exist in this version. thanks in advance.

---

### Post by rarsa on 2009-01-10
In the menu "System | Administration | Login window"

in the "Security" tab.

---

### Post by vautrin44 on 2009-02-10
Go to System/Control Center

It´s there under System

You´ll also find the Synaptic Package Manager there.

---

### Post by Frodgey on 2009-06-24
I have just enabled auto login in Jaunty - and the GUI has disapperared - just a black screen with a pointer.  Lucky I have a laptop as well.

How do I disable the auto login from the terminal?

Thanks in advance.

---

### Post by mtn on 2009-12-01
> **Frodgey said:**
> I have just enabled auto login in Jaunty - and the GUI has disapperared - just a black screen with a pointer.  Lucky I have a laptop as well.

How do I disable the auto login from the terminal?

Thanks in advance.

I have the same question.

I'm running Ubuntu Karmic 9.10 desktop on my laptop. I have the home folder set up as encrypted and so it needs the password when I login. I was doing something earlier (can't even remember what now) and in a pop up, was offered the option to "auto login" - I forgot I needed to login to unencrypt my home folder. A few hours later I restarted the laptop and  now I get errors at start up. How can I stop the auto login option through the terminal?

---

### Post by Megafag on 2009-12-01
> **Frodgey said:**
> I have just enabled auto login in Jaunty - and the GUI has disapperared - just a black screen with a pointer.  Lucky I have a laptop as well.

How do I disable the auto login from the terminal?

Thanks in advance.

if you can use terminal perhaps try using "startx" and following the above advice.

---

### Post by mtn on 2009-12-01
> **mtn said:**
> I have the same question.

I'm running Ubuntu Karmic 9.10 desktop on my laptop. I have the home folder set up as encrypted and so it needs the password when I login. I was doing something earlier (can't even remember what now) and in a pop up, was offered the option to "auto login" - I forgot I needed to login to unencrypt my home folder. A few hours later I restarted the laptop and  now I get errors at start up. How can I stop the auto login option through the terminal?

I fixed my problem. Bit of a convoluted way to do things, but it worked...

After booting up the laptop, it booted to a "blank" desktop - i.e. just the background image, and threw up errors. However, pressing the hardware on/off switch on the laptop brought up options to "shutdown, restart, hibernated or suspend". I chose hibernate. After it went in to hibernate, I turned the machine off, and then on again with the hardware button, it resumed from hibernation asking for my user password, and offering a number of other options "leave message, switch user" etc. I chose "switch user" and logged in a guest user (which I think I must have set up during install). Logging in as guest got me in to a working desktop and from here I disabled "auto login" - everything is back to normal now.

Btw, i tried everything I could thing of to get a working terminal - booting in to rescue mode ect but could not get a working terminal fro one reason or another. The solution above was a last desperate attempt - before reinstalling

---

### Post by Lefke123 on 2010-01-08
I hope I can still be of help to some people (that have encrypted folder and activated auto login). These are the steps that I followed to fix the problem:

1) logged in
2) startx
3) sudo gedit /etc/gdm/custom.conf
4) changed AutomaticLoginEnable to false

Fixes your problem...

---

### Post by nadeepa on 2010-02-04
What I did was,

1. when the blank screen appears, ctrl+alt+F1
2. log in
3. sudo vi /etc/gdm/custom.conf
4. changed AutomaticLoginEnable to false (you'll have to press 'i' for insert)
5. save (Esc -> :wq)
6. sudo reboot

You'll see login screen now!

---

### Post by philpool on 2010-02-08
Awesome. Thanks for pointing me to the custom.conf file. Cheers

---

### Post by thahir1986 on 2010-06-27
threre is no custom.conf file with in the /etc/gdm folder...shall i create the new one or i can use the gdm.conf file for this purpose.

thanks

---

### Post by thahir1986 on 2010-06-27
In /etc/gdm/gdm.conf file, i found the 

AutomaticLoginEnable , and i setup this as true and in the next line  AutomaticLogin , set the username...it's works 

Thanks people to show me the configuration file within the gdm  folder ...there are lots of stuff within this file..i will do more and learn more...

---

### Post by denovembre on 2010-10-17
very good, thank you

[http://blog.denovembre.com](http://blog.denovembre.com)

---


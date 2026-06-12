---
title: "Ubuntu won't let me log in"
date: 2008-08-10
forum: General Help
---

### Post by harryliddic on 2008-08-10
I am writing from windows because Hardy keeps asking for my password. It seems to accept it then the password screen reappears
over and over again. I was going to boot up in recovery mode but then I realized that I wouldn't know what to do once I got the prompt. I have a time critical project in Hardy and I need to get back to it. Any help will be appreciated.

---

### Post by berthiggins on 2008-08-10
boot into the recovery mode by pressing escape and selecting it at boot time 
then type passwd yourusername ( where yourusername is the name you log in as)for instance if the greeter says John Doe then it is probably John.

type your new password twice when asked then press controll alt delete to reboot.

---

### Post by WRDN on 2008-08-10
> **berthiggins said:**
> boot into the recovery mode by pressing escape and selecting it at boot time 
then type passwd yourusername ( where yourusername is the name you log in as)for instance if the greeter says John Doe then it is probably John.

type your new password twice when asked then press controll alt delete to reboot.

Rather than rebooting, you can just type "exit" and you return to the Recovery Mode options screen. Then just select "Continue Normal Boot".

---

### Post by PmDematagoda on 2008-08-10
> **harryliddic said:**
> I am writing from windows because Hardy keeps asking for my password. It seems to accept it then the password screen reappears
over and over again. I was going to boot up in recovery mode but then I realized that I wouldn't know what to do once I got the prompt. I have a time critical project in Hardy and I need to get back to it. Any help will be appreciated.

Boot Ubuntu in the normal way, then do these:-
1) Switch to a virtual terminal by pressing Ctrl+Alt+F1 and login to that.

2) Stop GDM with:-
```
sudo /etc/init.d/gdm stop
```

3) Start the X-Server manually with:-
```
startx
```

NOTE:- Starting X manually may have a few side-effects concerning GNOME and the way it functions, but otherwise it should work just fine.

---

### Post by harryliddic on 2008-08-10
I tried the above and came up with a "Fatal server error" and some message that my display was 0. I would have cut and pasted it but I was limited and my patience hardly hardy.

---

### Post by berthiggins on 2008-08-10
assuming that you have run the passwd command then just restart it should now work.

---

### Post by harryliddic on 2008-08-10
No such luck, the password is good it's the OS that isn't. I have given over two hours of my life for nothing. I should be walking the dog not trying to get to my work which is due tomorrow. I'll carry this rant on in private. Is it time to pull out the 8.04 install disk or is the problem worse than that?

---

### Post by PmDematagoda on 2008-08-10
> **harryliddic said:**
> No such luck, the password is good it's the OS that isn't. I have given over two hours of my life for nothing. I should be walking the dog not trying to get to my work which is due tomorrow. I'll carry this rant on in private. Is it time to pull out the 8.04 install disk or is the problem worse than that?

Try making a new user with:-
```
sudo adduser name-of-user
```
and then try logging in as the new user and see if that works atleast.

---

### Post by harryliddic on 2008-08-10
It didn't work, I logged in as fuzzy and with an appropiate password and the same do-loop of repeatingly asking me for my password continued.

---

### Post by hgfdsa on 2008-08-10
> **harryliddic said:**
> It didn't work, I logged in as fuzzy and with an appropiate password and the same do-loop of repeatingly asking me for my password continued.

If you have /home as a separate partition, wouldn't you be able to reinstall and keep your files?

---

### Post by MaindotC on 2008-08-10
Do you recall if you added the proposed and backports repositories in synaptic?  I ran into a similiar problem like this and it was because I downloaded stuff that was still in development.  Just a thought.

Anyway, I want you to get to your work which is due tomorrow and get it all done and completed but this is a good time to learn a couple things in the Psychocats tutorials.  Creating a backup image, creating a custom install cd (with all updates and packages), and putting the /home directory on its own partition.

Learning how to recover from this situation can be very time consuming but may be more beneficial in the long run.  For right now, I suggest you boot from the live cd, create a partition that you can backup any pertinent documents you need (or perhaps you have a usb drive?), then reinstall.  Although it just gives you a band-aid, it doesn't really provide a solution to your current problem, it will consume less time and get you to bed on time.  

After you reinstall, get it customized just as you like it and allocate time to learn about creating a backup image or putting the /home directory on its own partition.  Don't mess w/ the video driver configuration (godforbid), don't mess with user permissions or settings, just get it as you want it and make a backup of it.  Pscyhocats.net - great place for step-by-step tutorials on this stuff.

---

### Post by Danw12 on 2008-08-10
Use your live cd to acsess and recover your files (may take a while), and until you work out how to log in, use your livecd.

(First Post, so please tell me if i helped)

---

### Post by harryliddic on 2008-08-10
I don't know. I have /home as just another file in the root heirarchy. Does a 8.04 disk bother them?

---

### Post by MaindotC on 2008-08-11
It's not going to bother anything unless you modify them yourself.  When you boot with the 8.04 disk, you will see a filesystem associated w/ the live cd.  You will also have the option to access the filesystem that already exists on the hard drive where Ubuntu is installed.

When you use the live cd, you will be able to access the file system that has your documents and open or edit them as you wish.  You can also use this method to move the documents to a separate partition, which you can create if you don't already have one, or a usb drive, so you can reinstall the operating system.

Does that make sense?

---

### Post by m1keh on 2011-10-16
Try to log in into a console (ctrl alt f1), and log in.  This usually happens when one of your startup scripts throw an error..  See which script throws an error (or warning)' and try to fix that.

---

### Post by mörgæs on 2011-10-16
Thanks, but there is no need for answering a three years old thread.
Thread closed.

---


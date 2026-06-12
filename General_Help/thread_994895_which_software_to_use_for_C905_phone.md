---
title: "which software to use for C905 phone?"
date: 2008-11-27
forum: General Help
---

### Post by ramona000 on 2008-11-27
Hello,
I am new to this forum and hope I post my question in the right categorie. I will get the C905 Sony Ericcson phone next week. I sent an email to sony ericcson and they told me the pc suite doesn't support any linux OS. Can someone tell/explain me which ubuntu/linux software I can use for syncronising etc? I would be really grateful for any information. I have 8.10 on my laptop ( only 512 ram, it is the acer 3003 wlci laptop)
thx ramona

---

### Post by Kevbert on 2008-11-27
Welcome to Ubuntu.
You could try running the PC suite through wine (in the repos). Another piece of software that may help in gammu/wammu which again you can get via the repos/Synaptic Package Manager (the C902 works, so there's no reason why the C905 won't). The gammu database for phones is [[COLOR="Red"]here[/COLOR]]("http://cihar.com/gammu/phonedb/sony-ericsson/"). Please add your phone and what works/fails to the database when you try it out. It's strange that the C905 is actually made by HTC (for SonyEricsson) and all their phones don't work (mine included).

---

### Post by ramona000 on 2008-11-27
thanks a lot, i will try it. actually, i tryed with my current sony ericcson phone to install the pc suite via wine, but that wasn't working :-( I might have come back to you, as i am not sure how to set up that wammu software. i give it a try first, if i don't get it run, i ask again. thx again for the quick reply!

---

### Post by Kevbert on 2008-11-27
Just retried PC Suite with my K800i and it doesn't work with the current version of Wine. Part of the problem is that in Windows the PC Suite starts up as soon as you go into windows and sits in the background. This does not occur in Ubuntu with Wine.
With Gammu/Wammu you can sync the address book, phone numbers and some types of calls. I assume this is what you are after.
If you want to upload tones and pictures, you can do this with the Nautilus filemanager (comes with Ubuntu by default) via the USB cable.
Bluetooth can be a little troublesome as there are a few bugs to be sorted out.

---

### Post by ramona000 on 2008-12-02
finally i received my phone, but gammu or gmediamanager arn't working with my c905. i also tried installing either my phone explorer or pc suite...unfortunatly no luck...some has an idea? maybe?
would be great!

---

### Post by Vangelis on 2008-12-26
Yep, I can confirm that it doesn't work. This is very frustrating. My old K800i worked just like a USB memory stick. Comes up with the drive and all you have to do is transfer files to/from it. The stoopid C905 has stuffed up this simple and easy functionality. Why, oh why, do these - what can only be described as idiots - ruin something that works so well. I managed to download pictures from the phone but that's about it.

If anyone manages to get this working, I would be interested in knowing what the solution is.

Kind Regards,

Vangelis

---

### Post by chairmeleon on 2009-01-19
Check [this post]("http://www.uhl.nu/jesper/?p=61") in my blog to see a solution that applies to Ubuntu 8.10/SE C905 and possibly other recent SE phones.

---

### Post by monkeychick on 2009-01-23
I followed the instructions on the blog posted above and it seems to work with my phone (c905) my memory card shows up on the desktop when I selct mass storage.

---

### Post by Briped on 2009-03-07
I followed the guide too ([http://www.uhl.nu/jesper/?p=61](http://www.uhl.nu/jesper/?p=61)), but the terminal told me to sit on my hands, basically:

britta@britta-desktop:~$ cd /etc/udev/rules.d/
britta@britta-desktop:/etc/udev/rules.d$ rm 60-persistent-storage.rules
rm: remove write-protected regular file `60-persistent-storage.rules'? y
rm: cannot remove `60-persistent-storage.rules': Permission denied
britta@britta-desktop:/etc/udev/rules.d$ sudo rm 60-persistent-storage.rules
[sudo] password for britta: 
britta@britta-desktop:/etc/udev/rules.d$ wget [http://arch.uhl.nu/60-persistent-storage.rules](http://arch.uhl.nu/60-persistent-storage.rules)
--2009-03-07 08:11:41--  [http://arch.uhl.nu/60-persistent-storage.rules](http://arch.uhl.nu/60-persistent-storage.rules)
Resolving arch.uhl.nu... 212.97.132.138
Connecting to arch.uhl.nu|212.97.132.138|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3933 (3,8K) [text/plain]
60-persistent-storage.rules: Permission denied

Cannot write to `60-persistent-storage.rules' (Permission denied).
britta@britta-desktop:/etc/udev/rules.d$ 

So where do I go from here?

Thanks :)

---

### Post by inthevidual on 2009-06-02
I am the same poster as **chairmeleon** above, and as I am removing my old blog, I will post a link to the new (and updated) guide on my new home page.

**[http://inthevidual.com/wp/?p=61]("http://inthevidual.com/wp/?p=61")** - check it out!

---


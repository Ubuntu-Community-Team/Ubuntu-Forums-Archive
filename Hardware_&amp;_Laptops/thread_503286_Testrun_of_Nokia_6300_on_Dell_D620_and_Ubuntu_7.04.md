---
title: "Testrun of Nokia 6300 on Dell D620 and Ubuntu 7.04"
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by FerhatBingol on 2007-07-17
Hi,

Below text is from my blog. [http://linux.ferhatbingol.com/?p=21](http://linux.ferhatbingol.com/?p=21) 
I will update this text here and there, now and than. Please , add your experience if you have something for this triple. 

- Ubuntu 7.04
- Dell D620
- Nokia 6300



**Nokia 6300 on Dell D620 and Ubuntu 7.04**
I have bought a new cellphone, Nokia 6300. I wanted to see what can I do on Linux. I will update this text time to time when I can or cannot do something.

**USB Storage function**
Ubuntu recognized Nokia phone as USB storage device without no problem. I can browse, delete, create files like a USB stick. You can do anything you want over the files on the phone. Play mp3, edit pictures etc.

**USB Nokia Mode**
In phone mode Wammu has recognized it automatically and connected it. SPM has it ready to install. Install Gammu and Wammu.

*What I Can?*
- Retrieve phone info
- Retrieve Contacts from the SIM
- Retrieve Contacts from the phone
- Retrieve calls
- Retrieve messages
- Add/Edit new contact
- Backup everything OR just MSGs/Calls/Contacts
- Export messages as Email (file/folder)
[I]
What I cannot?[/I]
- Calender sync
- ToDo list access
- Send SMS
- Sync time of phone and PC

**Bluetooth**
If the Bluetooth server is running it recognize the device instantly. Than I used Bluetooth FileSharing 0.8 to send any file from my phone to Desktop. Work very well.

**Bluetooth Remote Control**
AnyRemote is a nice tool to control Linux remotely.

**SETUP :**

1) Download AnyRemote, AnyRemote Java Client and gAnyRemote from
[http://sourceforge.net/project/showfiles.php?group_id=162923](http://sourceforge.net/project/showfiles.php?group_id=162923)

2) Setup AnyRemote.

./configure

If you get

configure: error: cannot find install-sh or install.sh in . ./.. ./../..

That mean you need Automake version 1.9. Just setup it from SPM.

make

su "make install"

3) Setup Client on the phone. You can either compile again or just use the JAR file in /bin/anyremote. Worked perfect for me.

4) Setup gAnyRemote, just like below. No config.

su -c "make install"

**USAGE :**

1) run the server. Select a config file; under config examples directory there is a lot.

2) Run the java apllication on the phone.

3) Enjoy.

&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-
**NOT WORKING PART**

- Gnome phone manager (get a life)

---

### Post by aitorcalero on 2007-07-30
Hello, I have a d620 laptop also, but I don't know how can i make bluetooth working. It does not work for me. Did you do something special to make it work, or it just worked out of the box.
Any help will be much appreciated.;-)

---

### Post by desperado666 on 2007-07-30
How is it possible to connect my Nokia 6300 ? Cant access it through usb cable and wammu.

---

### Post by matt1606 on 2008-02-02
"I did setup on Gnome cause KDE sucks."

From Debian KDE user: KDE does not suck. It's your own opinion. Why are people so obtuse? - I don't know. I understand that I'm on a GNOME oriented forum but please...

---

### Post by pudgewack on 2008-02-02
This info is good to know.  I have a Nokia 5310 and a dell d620.  The only thing that I have tried is just mounting the microsdhc card to xfer music and photos (which worked perfectly).  It is nice to know that some of the other functions work outside of windoze.  I will try this sometime to make sure that it work on my 5310.

Thanks,
Matt

---

### Post by FerhatBingol on 2008-04-05
to matt1606

Matt, I agree with your comment. I do not know why I have written it that time. It must be one of my bad days. 

I am updating my post. 

cheers...

---


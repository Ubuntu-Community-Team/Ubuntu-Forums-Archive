---
title: "Bluetooth mouse won't work &quot;not a valid location&quot; &amp; &quot;HID create error&quot;"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by lcolson on 2007-10-19
My Kensignton PilotMouse Mini Bluetooth won't work in Ubuntu 7.10 Gutsy.  I recall it didn't work initially with feisty either, but I don't recall how I got it to work, I think I downloaded everything that mentioned bluetooth in add/remove to get it to work in feisty.

At any rate, when I click on the bluetooth icon on the top toolbar (after pushing connect button on my mouse), it shows up in the "Browse Devices" menu as "Kensington PocketMouse Bluetooth", but when I click "connect", it tells me 

"obex://[00:0c:55:02:8b:7f]" is not a valid location.  Please check the spelling and try again

SO not being daunted, I searched the forums and found commands for terminal like

#  hidd --search

which I ran and got the following message

Searching ...
        Connecting to device 00:0C:55:02:8B:7F
HID create error 13 (Permission denied)

Anyone have any ideas how to get my mouse to work?

---

### Post by nahham on 2007-10-19
Well the easiest way I found to make the mouse work is run the following: ```
 sudo hidd --connect xx:xx:xx:xx:xx:xx 
```.  You need to sudo the command. 

To make the mouse connect automatically every time you start Ubuntu, edit the bluetooth configuration file

```
sudo gedit /etc/default/bluetooth
```

find the following lines 

```

HIDD_ENABLED=0
HIDD_OPTIONS="-i XX:XX:XX:XX:XX:XX --server"

```

and change to

```

HIDD_ENABLED=1
HIDD_OPTIONS="-i XX:XX:XX:XX:XX:XX --server"

```

(replacing XX:XX:XX:XX:XX:XX with your mouse address)

The next time you start Ubuntu, it will tell you that the mouse is trying to access whatever and if you like to grant it access, answer yes and everything should work..

---

### Post by steveneddy on 2007-10-19
First read [URL="http://www.linuxquestions.org/linux/answers
/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu"]this[/URL].

Then read [this]("https://help.ubuntu.com/community/BluetoothSetup").

The first one talks about changing the password and making it auto. Very important.

The most important thing in the second one is the last command, loading the modules is the key to success.

:popcorn:

---

### Post by lcolson on 2007-10-20
First, thanks to both of you.  The first comment allowed me to get my mouse to work in the session, and the second link in the second comment got it to work whenever I restarted, just as it had before I updated.

One thing left though, just as before when I used feisty, when I restart in Gutsy, I actually have to turn my mouse off and back on again before it is recognized.  Any ideas how to get rid of this, so when the computer restarts it just recognizes the mouse?

---

### Post by nahham on 2007-10-20
I forgot to mention that the way I mentioned earlier worked flawlessly with my Microsoft IntelliMouse which did not require authorization.

---

### Post by tomdkat on 2007-10-31
> **steveneddy said:**
> First read [this]("http://www.linuxquestions.org/linux/answers//Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu").This appears to be a dead link.

EDIT:  The link is now working.  I think there is break after "answers" in the original URL that caused  my access problem.

> Then read [this]("https://help.ubuntu.com/community/BluetoothSetup").
This appears to be the "magical" link since it solved my problem!  Thanks!  :)

Peace...

---

### Post by oniichan on 2007-11-02
I have the same mouse. The Bluetooth applet is not working properly. And searching for it doesn't seem to work. I forced it and it worked immediately. For you it will be:

 sudo hidd --server -t 2 --connect 00:0c:55:02:8b:7f 

this makes sure the server is working, gives it two minutes to make happy, and is a direct connect. If this fails, it appears there is a permissions problem that was created with your install. You can also remove the Bluetooth applet COMPLETELY and then get the package again. That worked too. But I would like someone to tell me why the applet is scewing up.

---

### Post by ivelasco on 2007-12-03
> **oniichan said:**
> I have the same mouse. The Bluetooth applet is not working properly. And searching for it doesn't seem to work. I forced it and it worked immediately. For you it will be:

 sudo hidd --server -t 2 --connect 00:0c:55:02:8b:7f 

this makes sure the server is working, gives it two minutes to make happy, and is a direct connect. If this fails, it appears there is a permissions problem that was created with your install. You can also remove the Bluetooth applet COMPLETELY and then get the package again. That worked too. But I would like someone to tell me why the applet is scewing up.

You are my man!

in Feisty,edgy,dapper and so I had my bluez mouse working with some tweaks but unfortunately I couldn,t connect with it under gutsy...until I see your post.I connect it To the first attempt.


thanks

---


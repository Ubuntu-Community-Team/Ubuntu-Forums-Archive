---
title: "I am unable to connect to my wireless network."
date: 2006-03-23
forum: Hardware &amp; Laptops
---

### Post by Tokimasa on 2006-03-23
I have a Linksys Wireless-G USB Network Adaptor with SpeedBooster (model: WUSB54GS). I did not configure this during the install because I did not have everything that I needed (mainly my WEP key).

Now, I go into the Networking menu and select the wlan0 properties. I enter my SSID into the ESSID box. I then need to enter my WEP key *#:*#:*#:*#:## (* is a letter F, D, A, or C and # is a digit). I change the mode to Hex and enter the sequence without the colons. I then set the mode to DHwhatever (forgot the name right now) because that's how my Windows and Router settings are, so I figure it will work in Ubuntu. It works for a few minutes and then in the panel it says that the connection is active. However, when I go to Firefox and try to go to a website, it won't load because I don't have a connection.

What can I do? I would like to get on the internet with Ubuntu.

EDIT 1: I have searched the forums before posting this. However, the other topics suggest downloading something. More detailed instructions on what to download, where to download it, and how to install/set it up would be great. Thanks.

---

### Post by Jason_25 on 2006-03-23
Post the output of 
```

sudo iwconfig

```
Pay attention to the encryption part.  If it isn't right try 
```

sudo iwconfig wlan0 key insertkeyhere

```

---

### Post by Tokimasa on 2006-03-23
I'm new to Linux...where do I enter those commands? The console?

---

### Post by int on 2006-03-23
[QUOTE=Tokimasa]I'm new to Linux...where do I enter those commands? The console?[/QUOTE]

Please use the search button...

Yes is in the console, all comands are enter in there..

Not *sudp* but *sudo*

---


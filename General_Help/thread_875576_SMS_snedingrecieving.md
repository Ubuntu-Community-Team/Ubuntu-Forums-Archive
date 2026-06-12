---
title: "SMS sneding/recieving"
date: 2008-07-31
forum: General Help
---

### Post by randipoling on 2008-07-31
So on Yahoo, I can send and recieve SMS messages, when on Windows.  Is there a program for Ubuntu that i can use to send and recieve sms messages?

---

### Post by kgk on 2008-07-31
> **randipoling said:**
> So on Yahoo, I can send and recieve SMS messages, when on Windows.  Is there a program for Ubuntu that i can use to send and recieve sms messages?

I know you can send and receive SMS messages with Skype.

Sending them costs money I believe, but I don't think it costs anything to receive them.

Anyway, here's a post on the Skype forums about how to send an SMS message to a Skype user:

[http://forum.skype.com/index.php?showtopic=67564](http://forum.skype.com/index.php?showtopic=67564)



_Ignore this is you know how to install Skype on Ubuntu_, 

but there have been quite a few threads on various forums about people being stumped as to installing Skype, so might as well post it at the bottom here:

Skype won't install from the standard repositories with apt-get, you need to add them under Software Sources (System-Administration-Software Sources)

Click "Third-Party Software" tab.

Click "+Add"

Paste the following in the URL space:  [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/)

Click OK

Close the Software Sources window.  (It might say "blah blah out of date, update now?" Click yes)

Open Terminal (Applications-Accessories-Terminal)

Type > sudo apt-get update

Then type > sudo apt-get install skype

It will be under Applications-Internet.

---


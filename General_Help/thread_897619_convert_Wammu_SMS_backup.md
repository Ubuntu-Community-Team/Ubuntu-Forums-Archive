---
title: "convert Wammu SMS backup?"
date: 2008-08-22
forum: General Help
---

### Post by bryonak on 2008-08-22
Hi everyone,

I've started using Wammu to manage my Sony Ericsson k750i and, among other things, to back up the text messages when the phone memory gets full.
Now there are only two options: either export the messages in the Gammu SMS backup format or store them as an email.

While the latter is completely useless to me (I don't want to read those messages in an email client or send them to anyone), the first option has the drawback that only Wammu (or Gammu...) can present them in a sensible way (stripping out all the "gibberish" in between ;)).
But this only works if I first load them into the phone and view them there (with Wammu), which is not an option since this takes up the phone memory, which isn't empty anymore by now.

I really hope somebody could point out that I'm missing something simple, but I can't find any way to store the messages in "human readable plain text" or (preferably) HTML.
Any converting tools out there?

Thanks for your time.

---

### Post by bryonak on 2008-08-24
Still searching...

Can anyone recommend a tool that lets me backup the text messages directly?

(KMobileTools fails on my phone for some reason, and I'd prefer a GTK application if possible)

---

### Post by 3dmatrix on 2009-07-29
I am also interested in this information. The sms export file is very difficult to read. Can any one help ?

---

### Post by RodGer GR on 2009-11-23
Wammu has an option to export the messages to xml. I don't know if it is a new feature but I have problems with it. The problem is when I want to read the xml file where I get the following error in my browser window:
"XML Parsing Error: mismatched tag. Expected: </br>."

I tried to find the line where this is and finally I managed to make the file readable but all the messages are together, in plain text and without any formatting or at least a new line between them.

Should I file a bug? Is there a better workaround?

I just saw that there is also an option to read messages from the backup file but this gives an error too.
"Error while reading backup. Description: Unknown error. Function :ReadSMSBackup. Error code: 27"
I choose to report the bug from the little error window but it takes me to a firefox page with the "untrusted connection" message. Is there a problem with  "bugs.cihar.com" too?

Any suggestions for any of the above? What should I do?

--------------- System information ----------------(from wammu.log)
Platform     linux2
Python       2.6.4
wxPython     2.8.10.1
Wammu        0.30.1
python-gammu 1.24.0
Gammu        1.24.0
Bluetooth    PyBluez
locales      en_GB (UTF8)
connection   at
device       /dev/ttyACM0
model

---

### Post by Rytron on 2011-09-30
Wammu is a great tool but has some downfalls. A friend wants to backup all his SMS messages. I used Wammu to do this.

I did backup messages in these formats:
SMSmessages.backup
SMSmessages.mbox
SMSmessages.smsbackup
SMSmessages.xml

The problem is that I cannot then read these messages when I am not connected to the phone. How do I read those backup files with Gammu\Wammu? I want to read the messages in human readable format without all the gibberish.
If I have these messages backed-up like above, is it then safe to delete all the text messages from the cell\mobile phone?

Thanks.

---


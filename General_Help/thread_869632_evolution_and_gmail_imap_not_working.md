---
title: "evolution and gmail imap not working"
date: 2008-07-25
forum: General Help
---

### Post by supremearyal on 2008-07-25
I have set up evolution with gmail imap. Prior to imap, i had pop enabled. Now it says:

Error while Scanning folders in "IMAP server imap.gmail.com"

when trying to receive email. When I had pop enabled, I was able to receive email. The console output when running evolution from the terminal is:

evolution-shell-Message: Killing old version of evolution-data-server...
BBDB spinning up...

(evolution:9026): camel-CRITICAL **: camel_object_is: assertion `o != NULL' failed

(evolution:9026): camel-CRITICAL **: camel_object_unref: assertion `CAMEL_IS_OBJECT(o)' failed
Making error

I also have not been able to connect with pidgin, transmission, or use gnome-dictionary. I can, however, get on the internet with Firefox. I am running Ubuntu Hardy Heron. I do not have any firewalls setup. I installed Ubuntu yesterday. Any help on this problem would be greatly appreciated. Is it also normal for rhythmbox to be not able to play music while playing frozen-bubble.

---

### Post by lhaeh on 2009-11-04
I switched it form TLS to SSL and it started working, had to restart evolution though.

---

### Post by robbienam on 2010-09-10
The above solution of using SSL encryption for Receiving Mail resolved my problem as well. I had received the same error message as the above poster.

However, I found that selecting SSL encryption for Sending Mail did NOT work. It failed to send the mail and returned a generic error message with no explanation.

Then I tried switching Sending Mail to TSL encryption and it worked! I retested and got a repeat of the error trying to send with SSL, and again was solved by sending with TSL.

So in summary the settings which are working for my gmail IMAP within Evolution are:

Receiving Mail: SSL encryption

Sending Mail: TSL encryption

For more detailed discussion also see thread:

[http://ubuntuforums.org/showthread.php?p=9828326](http://ubuntuforums.org/showthread.php?p=9828326)

---


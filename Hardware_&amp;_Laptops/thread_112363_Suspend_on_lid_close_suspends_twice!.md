---
title: "Suspend on lid close suspends twice!"
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by Jeff250 on 2006-01-04
I have a Dell XPS m140, and the suspend function itself works great.  However, no matter which way I try to get it to suspend properly on lid close, it always suspends twice.  That is to say, I'll close the lid, and it will suspend.  Then I will open it, log in, and then it will suspend again!  So then I have to press the power button to resume.

I've tried copying /etc/acpi/sleep.sh to /etc/acpi/lid.sh and editing /etc/acpi/events/lidbtn to point to sleep.sh, but Ubuntu still suspends twice.

If I had to speculate, I would say that the lid open signal is mistakenly launching the sleep script instead of just the lid close signal, but I don't know how to get around this.  Can anyone help?  Thanks.

---

### Post by Jeff250 on 2006-01-06
After looking and playing around with files, I found a solution:
At a terminal, run:
```
sudo acpi_listen
```
Now close and open your laptop lid.  Press ctrl-c to stop acpi_listen.  You should now have list of various events.  Of most importance are the lid events.  It should look something like this:
```
button/lid LID 00000080 00000001
...
button/lid LID 00000080 00000002
...

```
Since this is listed chronologically, the first lid entry must be the close and the second must be the open.  Knowing this, we can set it to only suspend on the close.  Type the following:
```
sudo gedit /etc/acpi/events/lidbtn
```
Comment out the current "event=" line and replace it with a new one equalling to the first lid event (the lid close) that was listed earlier.  It should look something like this:
```
# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

#event=button[ /]lid
event=button/lid LID 00000080 00000001
action=/etc/acpi/lid.sh
```
I have the event run lid.sh instead of sleep.sh because I copied sleep.sh over lid.sh, but, if you haven't done this, change lid.sh to sleep.sh in order for it to actually suspend on lid close instead of what it does otherwise.

Now save the file, and *reboot*.  Now your suspend will only run on lid close instead of any lid action.  It should only run once now when you close and open your lid instead of twice!

---

### Post by spier on 2006-01-06
Great catch, Jeff,  worked like a charm!

Now I can close my lid and walk around with my laptop under the arm safely!

Thanks for the tip!

---


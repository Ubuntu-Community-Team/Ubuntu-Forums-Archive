---
title: "Closing laptop lid has not the desired effect"
date: 2008-11-26
forum: Hardware
---

### Post by Ouguiya on 2008-11-26
Good day and hello.

There is a small problem where I once again require your help.

The problem is a simple one, but I haven't been able to solve it yet.

Description: Even when set up in gnome power manager, closing the laptop lid produces no effect. My initial idea was to make the laptop suspend when closing the lid. I thought it very cool that the option to do so was so easily accessible via the gnome power manager. However, even when setting it to suspend or hibernate (or whatever) closing the laptop lid causes no reaction.

It should be noted here that suspension, hibernation, etc. all function perfectly well, when they are used manually via the exit function from the gnome panel, but sadly not when closing the laptop lid.

I have searched the internet a bit, and found out that this appears to be a problem which happens somewhat often, but haven't been able to pin down a solution as of yet.

Thus, it is my hope that someone in the Ubuntu forums knows how to beat this bug.


Hardware specifications: The laptop I am currently using is the "Sony Vaio - VGN-SZ61VN", which was released around 1 1/2 years ago.

I have (as mostly) packed further hardware information about my computer in a html format and uploaded here, since it does appear to be a hardware problem after all.

Thank you in advance for all replies.

Yours,

Ouguiya

---

### Post by sdennie on 2008-11-26
It could be that the lid button event isn't being generated correctly.  After closing the lid, have a look at the bottom of /var/log/acpid and see if there are any messages about the lid button event.

---

### Post by Ouguiya on 2008-11-26
Dear vor,

Thanks for the quick replay. I tried to do what you told me, but failed, sadly, since there appears to be no acpid in the log folder.

I tried to take a look at the logs from the "System log" under the "administration panel", but found nothing noteworthy there.

Do I need a special tool or something to write this log?

Thanks again.

Yours,

Ouguiya

---

### Post by Ouguiya on 2008-11-27
Bump - Sadly, I'm still fighting with that problem. Does anyone have any idea how to resolve this?

---

### Post by sdennie on 2008-11-27
> **Ouguiya said:**
> 
Thanks for the quick replay. I tried to do what you told me, but failed, sadly, since there appears to be no acpid in the log folder.


That could actually be the problem then.  What is the output of:

```

ps aux | grep acpi

```

Also, go to System->Administration->Services and make sure that "Power Management" is turn on.

---

### Post by Ouguiya on 2008-11-27
Hello again! Thank you for the reply.

I have executed the command you asked me, and this is the output:

ouguiya@ouguiya-laptop:~$ ps aux | grep acpi
root        57  0.0  0.0      0     0 ?        S<   19:01   0:00 [kacpid]
root        58  0.0  0.0      0     0 ?        S<   19:01   0:00 [kacpi_notify]
root      5448  0.0  0.0   2308  1216 ?        Ss   19:02   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
111       6631  0.0  0.0   2296   900 ?        S    19:02   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
ouguiya  10168  0.0  0.0   3240   820 pts/1    S+   19:35   0:00 grep acpi


I do not really know what all the values mean, but I hope they tell you what's wrong.

I have also checked under "services" and both Power management(s) are enabled. (One labeled acpid, the other apmd)

Thanks again,

Yours,

Ouguiya

---

### Post by sdennie on 2008-11-27
That output looks correct to me.  Are you positive that you don't have a /var/log/acpid file?  Try:

```

gedit /var/log/acpid

```

---

### Post by Ouguiya on 2008-11-27
Hello again!

I entered your command as you stated, but this simply opens a blank page, ready for me to write something in, even when run with "sudo".

Does this make any sense to you?

Thanks again for the help.

Yours,

Ouguiya

Edit: I also post here the output of the "cat" command:

ouguiya@ouguiya-laptop:~$ cat /var/log/acpid
cat: /var/log/acpid: No such file or directory
ouguiya@ouguiya-laptop:~$

---

### Post by Ouguiya on 2008-11-28
Bump - It's incredible how fast posts go to the 6th or even worse page.

---


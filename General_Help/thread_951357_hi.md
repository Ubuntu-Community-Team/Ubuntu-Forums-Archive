---
title: "hi"
date: 2008-10-18
forum: General Help
---

### Post by digambar.patankar on 2008-10-18
Hi, I am very new to DBUS.
I have written some application using DBUS. when i run the program i am getting the errors like this.
arguments to dbus_message_new_signal() were incorrect, assertion "_dbus_check_is_valid_path (path)" failed in file dbus-message.c line 1161.
This is normally a bug in some application using the D-Bus library.
process 6000: arguments to dbus_message_append_args() were incorrect, assertion "message != NULL" failed in file dbus-message.c line 1489.
This is normally a bug in some application using the D-Bus library.
process 6000: arguments to dbus_connection_send() were incorrect, assertion "message != NULL" failed in file dbus-connection.c line 3082.
This is normally a bug in some application using the D-Bus library.

anybody help, will be appreciated.


thanks

---

### Post by Ryadt on 2008-10-18
Can you please use a descriptive title......

---

### Post by PocketDog on 2008-10-18
Did you log the query?

---

### Post by digambar.patankar on 2008-10-20
> **PocketDog said:**
> Did you log the query?

how to log the query?

---

### Post by digambar.patankar on 2008-10-20
> **Ryadt said:**
> Can you please use a descriptive title......

i have two program.listen and send.i am trying to send a signal which should be received in other application through dbus. i have a doubt that the object and interface which are sending and receiving signals have to be registered with dbus or we can just use any name for object and interface in the code.please clarify my doubt..inspiteof this i am getting the errors as already posted while running send program
any help appricieted

---

### Post by jespdj on 2008-10-20
What Ryadt meant is that you should not use a title like "hi" for your post. Instead, use a one-line description of your problem. For example:

"DBUS programming question, failed assertions"

And this question fits better in the [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39) forum than in the General Support forum.

The errors probably mean that you are calling some functions with wrong arguments. Can you post your code? Because it's very hard to say what you're doing wrong exactly without seeing your code.

---


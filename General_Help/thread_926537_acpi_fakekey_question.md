---
title: "acpi_fakekey question"
date: 2008-09-22
forum: General Help
---

### Post by ezzieyguywuf on 2008-09-22
can someone help me understand the following "acpi_fakekey gets the key numbers for specific events generated as output by scripts in /etc/acpi/ and writes them to the correct input FIFO in /dev/input/eventx. " I understand that it gets a key number, but what does it then do with the key number? what happens after it get written in eventx and what is FIFO?

I'm trying to understand everything that happens when I press FN+F4, so let me tell you guys where I'm at so far in my understanding process and maybe you can help fill in some holes and whatnot. 

So, first acpi read the event in /etc/acpi/events/ibm-sleepbtn. this script calls /etc/acpi/sleepbtn.sh , which in turn sets a bunch of variables, and then runs acpi_fakekey $KEY_SLEEP . 

Heres is where I get lost. Why set all those variables, why not just run acpi_fakeky 112 (or whatever the variable happens to get set to). Also, why not just run acpi_fakekey in the same script as the events script? just to keep things organized?

---

### Post by ezzieyguywuf on 2008-09-27
bump

---

### Post by jeff.sadowski on 2010-02-20
Maybe I might be able to shine a little light on the subject. I would like to find where acpi_fakekey's source comes from I will do some more research. From studying the command structure and what it does I thing the man page that comes with ubuntu/debian is misleading and maybe even wrong. 

acpi_fakekey seems to be an awful lot like kbde although built in; but not as advanced. First: If you login as root ("sudo su -") you can play around with it. Second: As the scripts that are used with it do source the helpful variable name file ". /usr/share/acpi-support/key-constants" or "source /usr/share/acpi-support/key-constants". Then use "acpi_fakekey $KEY_A" you can see that it types an "a" you will need to backspace to get rid of it in order to run another command. If you examine the /usr/share/acpi-support/key-constants file you will see a list of keys it is suppose to understand. However I have been finding out that not all keycodes are understood. I will try and make a list of what I find out and see if anyone else can shed more light. I mapped an acpi event to a script and modify the script changing to each keycode and testing each with "showkey -s" on tty1 (get to it via Ctrl+Alt+F1 use Ctrl+Alt+F7 to get back to X windows) If it is an understood key showkey will display it.
I have been wondering how to get the keycodes that are not seen to be seen. I'd like to use the keycode $KEY_COFFEE or 152 as it would be more appropriate keycode to use for a lockscreen application. I use an alternate keycode that is displayed by showkey that is not mapped to any other key.

---


---
title: "Power Management Question"
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by DimitrisC on 2006-08-31
I have a dell inspiron 6000 laptop and ubuntu 6.06 installed.  Power managament is a mess! Hybernate doesn't work.  The laptop just shuts down but cannot resume.  Log out doesn't work either if i select it from the shutdown menu. It works great only if i CTRL-ALT-BACKSPACE. I want to ask if there is a way to make ubuntu shutdown when i close the laptop lid.  Now its just set at black screen.  
Thanks in advance!

---

### Post by Nicarlo on 2006-09-03
i also have a dell inspiron 6000 with ubuntu installed. Hibertnate doesnt seem to work for me also ( only sometimes ). The biggest problem i seem to be having is everytime i close my lid and open it again the screen doesnt come back and i have to CTRL-ALT-BACKSPACE to reboot the gui. I also have it to black screen but it just doesnt want to resume back. I tried setting the powermanagement to do nothing but that just did the same thing.. Anyone know how to go about fixing this problem ?

---

### Post by Brendt2 on 2006-09-03
This is a very good question.   I also wonder if we would have the ability to create events from the power buttons on our pc's. 

One of my desktops has two buttons.   In windows, I had the ability to change the event for the button.   So that if I hit the power button it would goto hibernate or whatever I desired.  My Ubuntu brings up a menu with choices... which doesn't work for me as I am running out of the room! Haha!

And of course similar abilities on laptops is key!

I guess where does one start to see the hardware interupt events for Ubuntu?

---

### Post by ianmac on 2007-02-21
try looking in the /etc/acpi directory.  You'll see scripts that are attached to various system power related events.

Ian

---


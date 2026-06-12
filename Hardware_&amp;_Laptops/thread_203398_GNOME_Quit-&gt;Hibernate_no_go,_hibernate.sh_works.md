---
title: "GNOME Quit-&gt;Hibernate no go, hibernate.sh works!?!?!?"
date: 2006-06-25
forum: Hardware &amp; Laptops
---

### Post by joseff on 2006-06-25
I just upgraded from Breezy to Dapper and first of all, I have to say that Dapper is MILES ahead in terms of functionality.  Kudos to the devs.

My laptop is an Acer Aspire 1682WLMi with intel 855GM and 2200BG.  I have one major problem with suspend though.  In my Breezy setup, I did this:

```
sudo mv /etc/acpi/powerbtn.sh /etc/acpi/powerbtn_default.sh
sudo ln -s /etc/acpi/hibernate.sh /etc/acpi/powerbtn.sh
```

And edited my GRUB menu.lst file accordingly (resume=swap_partition), update-grub etc.

And thus, a tap on the power button hibernates the laptop.  This works beautifully.

Now I found in Dapper that using the GNOME menu Quit -> Hibernate, the GUI goes wonky on resume.  Windows won't redraw, buttons disappear, etc.  Restarting X (Ctrl-Alt-Backspace) doesn't fix anything.

However, if I do:
```
sudo /etc/acpi/hibernate.sh
```

I find the computer hibernates and resumes perfectly.  But if I link /etc/acpi/powerbtn.sh to /etc/acpi/hibernate.sh as above, the GNOME Quit dialog still pops up.

My questions are:
- What is the difference between GNOME Hibernate button and hibernate.sh?  Is there a way to make the Hibernate button do hibernate.sh instead of whatever it is running? (is it hibernatebtn.sh?)
- Failing that, how do I prevent the GNOME Quit dialog from showing?  I much prefer the old behaviour of simply hibernating when I tap the power button.

---


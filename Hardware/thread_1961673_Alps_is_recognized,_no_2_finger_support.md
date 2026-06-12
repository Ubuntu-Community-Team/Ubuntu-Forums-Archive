---
title: "Alps is recognized, no 2 finger support"
date: 2012-04-19
forum: Hardware
---

### Post by DubelBoom on 2012-04-19
Hi!
After a lot of search, i finally made linux recognize my alps as GlidePoind, but - my Inspiron N5110 has TouchPoint that supports multi-fingers. so i changed the TouchPad name at alps.c and now its shown as TouchPoint, but Synaptiks still allows only one finger. so im thinking its something not related to the name.
Please help, its the only thing keeping me away from ubuntu and linux!

---

### Post by DubelBoom on 2012-04-20
*up*

please help..

---

### Post by quarara on 2012-04-22
> **DubelBoom said:**
> Hi!
After a lot of search, i finally made linux recognize my alps as GlidePoind, but - my Inspiron N5110 has TouchPoint that supports multi-fingers. so i changed the TouchPad name at alps.c and now its shown as TouchPoint, but Synaptiks still allows only one finger. so im thinking its something not related to the name.
Please help, its the only thing keeping me away from ubuntu and linux!
I'm sorry I can't help you, but have you succeeded enabling vertical scrolling on this laptop? How have you done it?
Thanks in advance!

---

### Post by DubelBoom on 2012-04-23
> **quarara said:**
> I'm sorry I can't help you, but have you succeeded enabling vertical scrolling on this laptop? How have you done it?
Thanks in advance!
i made Synaptiks work, and it has this option.
1. Download and install this: [http://dl.dropbox.com/u/22680754/psm...s_0.10_all.deb]("http://dl.dropbox.com/u/22680754/psmouse-alps-dkms_0.10_all.deb")
2. open terminal and write:[FONT=monospace]
[/FONT]cd /usr/src/psmouse-alps-0.10/src[FONT=monospace]
[/FONT]3. Now write:[FONT=monospace]
[/FONT]sudo gedit alps.c[FONT=monospace]
[/FONT]4. At the file look for the  /* Dell Vostro 1400 */ line, and  above it you'll see 0x73 , 0x02 , 0x50, replace the 0x02 with 0x03 and  save.
5. At the terminal, make sure your still at "/usr/src/psmouse-alps-0.10/src[FONT=monospace]" and write:
[/FONT]sudo dkms add -m psmouse -v alps-0.10
6. Write:[FONT=monospace]
[/FONT]sudo dkms build -m psmouse -v alps-0.10[FONT=monospace]
[/FONT]7. Write:[FONT=monospace]
[/FONT]sudo dkms install -m psmouse -v alps-0.10

Now reboot, open the terminal again and write "xinput list", you'll see "Alps/PS2 Alps GlidePoint".

now you need to install Synaptiks and enable it.



anyone has a fix for me?

---

### Post by miz0ooo0 on 2012-04-23
man ,i had this problem with this laptop when i was using ubuntu 11.10 _64bit_ but recently i upgraded to ubuntu 12.04 with _32bit_ ,then i find options for touchpad you can choose 2 fingers scrolling from it
i think 32bit "intel" more suitable for laptops

---

### Post by DubelBoom on 2012-04-24
> **miz0ooo0 said:**
> man ,i had this problem with this laptop when i was using ubuntu 11.10 _64bit_ but recently i upgraded to ubuntu 12.04 with _32bit_ ,then i find options for touchpad you can choose 2 fingers scrolling from it
i think 32bit "intel" more suitable for laptops
ill check it when the final 12.04 will be out, if this is true, its a bug ubuntu should fix. i do want all my 6GB ram available...

---

### Post by DubelBoom on 2012-04-27
*up*

12.04 didn't fix the problem...
how do i make linux know my touchpad recognize 4 fingers?!?!!?

---

### Post by quarara on 2012-05-02
Yup, I tried the workaround you proposed in another post, but it doesn't work for me neither.

---


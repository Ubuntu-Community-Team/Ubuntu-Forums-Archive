---
title: "Delete Button not working!"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by kthakore on 2006-06-09
I had a problem with the delete button in breezy, but it is continuing into drapper, and I am at a lost. I have changed keyboards and everything. here is the original thread:

[thread]("http://ubuntuforums.org/showthread.php?p=1118602#post1118602")

basically the only way I can get my delete buton to work is by changing the keyboard model in the preferences menu. But everytime i restart the keyboard again loses the delete button functionailty, but the numpad delete works. I am praying for an answer now[-o<

---

### Post by glotz on 2006-06-09
Do **cat /etc/X11/xorg.conf** and paste here your keyboard section. What changes do you make in prefs to make it work?

---

### Post by kthakore on 2006-06-09
here it is 

```
Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection
```

---

### Post by glotz on 2006-06-09
Yeah, now what do you change in prefs to make it work? What kind of keyboard is it anyways?

---

### Post by kthakore on 2006-06-09
its a generic internet keyboard qwerty, besides that I don't know

---

### Post by glotz on 2006-06-09
What layout does it work with?

---

### Post by kthakore on 2006-06-10
it works with logtiech internet feyboard, microsoft internet keyboard, and pretty much all of them

---

### Post by glotz on 2006-06-10
Try running **sudo dpkg-reconfigure xserver-xorg**

---

### Post by kthakore on 2006-07-12
I tried that but it still won't work

---

### Post by kolisikepu on 2008-03-26
I think this has come back to haunt us... or I don't think it was ever resolved.

My Delete button on my Acer Extensa 5220 Notebook does not work in Hardy.  It worked in Gutsy, but not in Hardy now.

Any ideas as to how I can fix this??

---


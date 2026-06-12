---
title: "[SOLVED] Problem with the double-quotes keyboard key"
date: 2008-09-03
forum: General Help
---

### Post by fast-Eddie on 2008-09-03
Hi,

I am new to Ubuntu and am using version 8.04. I have noticed that my keyboard double-quotes key (¨) doesn´t seem to be printing correctly in Ubuntu. I am just starting to learn perl in Ubuntu and it doesn´t like the symbol produced by my double-quotes key (¨). If however I copy double-quotes from other text and substitute all my double quotes with the copied ones, perl works fine. I am running Ubuntu in VMWARE player 2.0.5 (latest) on Vista. Within Vista, the double-quotes key works fine.

Any ideas??

Thanks.

---

### Post by Mister.Vash on 2008-09-03
Goto  System ->  Preferences -> Keyboard
Then go to the layouts tab
Make sure that they correct Keyboard Model is selected
Make sure that the Layout is correct.  If USA isn't what you want it set to, try the USA layout just for a comparison to see if it works

---

### Post by fast-Eddie on 2008-09-03
It took a little fiddling around to find the right one but it works now!!

Thank you very much!!

---

### Post by Pro-reason on 2008-09-03
You had the US-international keyboard selected.  Certain keys are “dead keys”, meaning that they do nothing by themselves but instead serve to add accents to other characters.  You were adding an accent known as an *umlaut* or *diæresis* (äëïöü) to a space (¨).

It is better to use the “AltGr” US-international variant.  That one only inputs accents when you press the right Alt key.  You can also just use a standard US layout, but then you will not be able to input accents, and some accents are necessary even to input English correctly (e.g. *résumé*).

---

### Post by fast-Eddie on 2008-09-03
I have indeed selected the US International layout and tested it as well and it does work as intended.

Thanks again.

---

### Post by bitumen on 2008-12-20
thanks 

selected was USA with dead keys

reselecting USA 

fix the missing double quote '"' miss printing

---


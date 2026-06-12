---
title: "HP function keys use to increase volume, decrease volume, etc..."
date: 2023-12-11
forum: Hardware
---

### Post by joep991 on 2023-12-11
HP keyboard function keys (f7, f8)  use to increase volume, decrease volume, etc...  
Now just something pops up about caret browsing when one is pushed.

Wonder how I lost this keyboard feature

Ubuntu 22.x lts user

---

### Post by Holger_Gehrke on 2023-12-11
Function keys used to emit specific keycodes that applications interpreted as calls to specific function (e.g. F1 is help, F10 is menu, F6 puts the cursor in the address bar in browsers ...). Then laptop manufacturers wanted to have multimedia keys on their keyboards but didn't want to add more keys to their keyboards, so they repurposed the function keys and put a key labeled "FN" on their keyboards to switch between the old behaviour of the function keys and their multimedia function. Usually there's an item in the firmware menus to switch whether the default is classic or modern function keys; on my laptop I had to switch it to classic behaviour because I use those a lot more often than the multimedia keys. Try holding the FN key and hitting F7 / F8, this should change the volume.

Holger

---

### Post by jimmyrus on 2023-12-11
> **joep991 said:**
> HP keyboard function keys (f7, f8)  use to increase volume, decrease volume, etc...  
Now just something pops up about caret browsing when one is pushed.

Wonder how I lost this keyboard feature

Ubuntu 22.x lts user
so what do we got to do to get you to actually tell us what the something that pops up is? Don't tell us what
hp you have either so did you bother to look at the fn keys or change something?

---

### Post by joep991 on 2023-12-12
If I hold the Fn key down, it will let me access the "modern" keys like increase volume and so forth - it use to be I didn't have to hold Fn down....

To answer the question, if I press F7 without Fn, it asks if I want to turn "caret browsing" on

Oh well, it's not that big of a deal....

---

### Post by jimmyrus on 2023-12-12
> **joep991 said:**
> If I hold the Fn key down, it will let me access the "modern" keys like increase volume and so forth - it use to be I didn't have to hold Fn down....

To answer the question, if I press F7 without Fn, it asks if I want to turn "caret browsing" on

Oh well, it's not that big of a deal....
still hadn't said what kind of laptop this is or what you changed because if it was working and now its not then
you did something. Prolly related to the keyboard layout but since we're having to play guessing games who 
knows?

and if you knew how to adjust the volume and its not a big deal to you why bother asking? try to look up
solutions or do you just want a handout?
[https://askubuntu.com/questions/818413/how-can-i-toggle-the-fn-function-key](https://askubuntu.com/questions/818413/how-can-i-toggle-the-fn-function-key)

---

### Post by Holger_Gehrke on 2023-12-12
Asking the [duck]("https://duckduckgo.com") for "Linux laptop keyboard function keys" brings up [this discussion on askubuntu]("https://askubuntu.com/questions/818413/how-can-i-toggle-the-fn-function-key#:%7E:text=Open"). Seems that some HP laptops use FN with the left shift key as toggle for the function keys. Worth a try at least. Might be mentioned in the manual for your model if they have something like that and what key it is (this would be a function of the hardware and independent of the OS used). It was also mentioned that most machines that have this kind of functionality have a menu item in UEFI / BIOS to make that change. Look up how to get into the firmware on our system and have a look.

Holger

---

### Post by jimmyrus on 2023-12-13
> **Holger_Gehrke said:**
> Asking the [duck]("https://duckduckgo.com") for "Linux laptop keyboard function keys" brings up [this discussion on askubuntu]("https://askubuntu.com/questions/818413/how-can-i-toggle-the-fn-function-key#:%7E:text=Open"). Seems that some HP laptops use FN with the left shift key as toggle for the function keys. Worth a try at least. Might be mentioned in the manual for your model if they have something like that and what key it is (this would be a function of the hardware and independent of the OS used). It was also mentioned that most machines that have this kind of functionality have a menu item in UEFI / BIOS to make that change. Look up how to get into the firmware on our system and have a look.

Holger
Ya..same one I found when I looked but the difference is that you and I both tried on our own. op never has and I dunno why they keep creating id's
and asking the same things other than just wanting attention.

---


---
title: "OpenOffice: How can I edit and use spell check in other languages? (spanish)"
date: 2005-11-07
forum: General Help
---

### Post by ThirdWorld on 2005-11-07
Please, can somebody help me with this one,  I cant find any info in OpenOffice website about it. 
I need a way to edit or do spell check in spanish or any other languages with open office like i do in MS office for windows because i have a webpage that i need to edit and update periodically and i want to do it in ubuntu.  :confused: 

Thank you

---

### Post by XDevHald on 2005-11-07
This link will be of some great help to you: [http://homepage.ntlworld.com/garryknight/linux/oodict.html](http://homepage.ntlworld.com/garryknight/linux/oodict.html)

Good Luck!

---

### Post by Svip on 2005-11-07
Well, according to OpenOffice.org, you should do Files -> Wizards -> Install New Dictionaries.

---

### Post by ThirdWorld on 2005-11-07
[QUOTE=Svip]Well, according to OpenOffice.org, you should do Files -> Wizards -> Install New Dictionaries.[/QUOTE]

i already tried the wizzard but everytime I did nothing happend. i will try to install the diccionaries manually, i wish it will be more simple like MS Office

---

### Post by Svip on 2005-11-07
[QUOTE=ThirdWorld]i already tried the wizzard but everytime I did nothing happend. i will try to install the diccionaries manually, i wish it will be more simple like MS Office[/QUOTE]
Simple? It took me days to find a Danish spellchecker for Microsoft Office, while it took me a few minutes to install a dictionary to OOo.

Mainly because Microsoft won't release the dictionaries to the public, so you have to know someone who has them. Or so it was in my case.

---

### Post by audax321 on 2005-11-07
Installing an additional language is very easy. For spanish you would install the following package from Synaptic:

myspell-es

OR

sudo apt-get install myspell-es


Then you can go to Tools > Options > Language Settings > Languages and select the Spanish language.

Installing it this way also gives you the spell check dictionary for different Spanish speaking countries as well.

---

### Post by ThirdWorld on 2005-11-07
[QUOTE=audax321]Installing an additional language is very easy. For spanish you would install the following package from Synaptic:

myspell-es

OR

sudo apt-get install myspell-es


Then you can go to Tools > Options > Language Settings > Languages and select the Spanish language.

Installing it this way also gives you the spell check dictionary for different Spanish speaking countries as well.[/QUOTE]

Holly Hecate, thanks audax, that was quite simple: synaptic --> myspell-es -->install --> start OpenOffice. Wow Thank you so much!! 

This solved my problem, thank you all again for your replies.

---


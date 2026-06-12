---
title: "[SOLVED] GEdit - Question on its Dictionary and spell-checker!"
date: 2008-11-24
forum: General Help
---

### Post by Rytron on 2008-11-24
Hi,
I use GEdit as my main text editor. I use the spell check and need to add such words as Ubuntu and Xubuntu(after a fresh install) that it does not recognise and underlines in red. Is there a way to backup the dictionary word list file it uses?

I want to back up the file that holds all the words I add so that I don't have to continually add new words that I know are spelled correctly after each install of Ubuntu.

Thanks.

---

### Post by Rytron on 2008-11-30
This would be a great time saver.

Anyone?

---

### Post by fragos on 2008-11-30
The dictionary might be en-US.dic

---

### Post by PersistentLurker on 2008-12-15
I think you want to look at ~/.config/enchant/

For me at least, that directory contains the "personal dictionaries" ( .dic files) for various languages. enchant, I believe, is the spell-check engine used by gedit.

HTH.

---

### Post by fragos on 2008-12-15
I have dic files in ~/.config/enchant but they are 0 length. My dictionary is located in /usr/share/myspell/dicts/en_US.dic. Spell check does work correctly for Gedit on my system.

---

### Post by PersistentLurker on 2008-12-15
> **fragos said:**
> I have dic files in ~/.config/enchant but they are 0 length. My dictionary is located in /usr/share/myspell/dicts/en_US.dic. Spell check does work correctly for Gedit on my system.

Well, all I can say for sure is that when I add a new word via "Add word" under "User dictionary" in gedit's "Check Spelling" dialogue, the word shows up in ~/.config/enchant/en.dic

But that certainly could depend on the version of gedit. I'm currently using the stock version in Ubuntu 8.10.

---

### Post by Rytron on 2008-12-16
> **PersistentLurker said:**
> Well, all I can say for sure is that when I add a new word via "Add word" under "User dictionary" in gedit's "Check Spelling" dialogue, the word shows up in ~/.config/enchant/en.dic

But that certainly could depend on the version of gedit. I'm currently using the stock version in Ubuntu 8.10.

I also have my newly added words in > ~/.config/enchant/en.dic

I tried to add a word manually to en.dic and then open a text file which had that word, it works. Also by deleting a word from en.dic and then trying the spellchecker that deleted word now shows up as a spelling error.
The word I used was Columbo(one of my favourite shows).

---


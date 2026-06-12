---
title: "Entering European Characters in Ubuntu"
date: 2008-11-15
forum: General Help
---

### Post by Euphorion on 2008-11-15
Hallo

I am stuck with this basic problem. I am using Ubuntu in English here in Germany with a German Keyboard Layout - all is working well.

What I want to know is how do I enter other European characters, for example French letters with accents, the Spanish ones with the wavy line on top.

In Windows I type Alt + 4 Digit number, this does not work in Ubuntu. What method do I have to use in Ubuntu

Thanks in advance

---

### Post by yopnono on 2008-11-15
[http://en.wikipedia.org/wiki/Compose_key](http://en.wikipedia.org/wiki/Compose_key)


On my dell I use the "Alt Gr" and "Alt gr + Shift" to get different characters, @&#322;&#8364; = "alt gr" qwe, &#937;&#321;¢ = "alt gr + shift" qwe

---

### Post by Euphorion on 2008-11-15
Thank you, I am reading the Wiki Link and will try the various key combinations and see if I can reach the keys that I require.

Update: I have tried all key with AltGr and AltGr + Shift I get many special characters like arrows, Yen sigh, Omega etc but not the ones that I require. I cannot get the French accented letters, or the Spanish letters.

The only other way seems to be to define the French and Spanish Keyboard layouts in System -> Preference -> Keyboard and then find a method of switching between the various keyboards. The only thing that remains is to find out how to switch the Keyboards about.

The other thing is to search the forums and Internet for topics concerning key mapping in Linux. I will also try a post in the German Forum, as I expect other Europeans must be having the same problems when using more than one language.

---

### Post by Euphorion on 2008-11-18
Solved !

I have found the following in Intrepid. Right click in a free space on the upper panel bar. Confirm add to panel. In the list there is an entry "insert special characters". Select this option. In the panel bar special characters out of all European characters sets are offered structured according to the alphabet. This is done via a down arrow with a drop down field.

Using this method I am now able to enter all the special characters which I require. When a special character is clicked it is placed in the clipboard and in the required application inserted using insert or Ctrl + V.

---

### Post by secretspicy15 on 2010-01-15
I've also ran into this problem -- English is my mothertongue, but I also speak german and am learning french; The way I've handled special characters it by switching keyboard layouts. I have my default set to USA (which is what my physical keyboard is), and have it set to switch to german while I hold my windows key (basically like an extra shift to input deutsch characters, like öäüß usw.), since that's the other one I use most. 

Then I have a Keyboard Layout Indicator on my gnome panel; it displays the current layout and you can easily switch by clicking on it, for example, if i'm typing something in french, or doing a lot of german, I can just switch.

This is, for me, easier than click click clicking to find every character I need...

---

### Post by LoneWolfJack on 2010-01-15
I'm not sure what you mean by "french accented letters", but if they are ó á ú, etc., you need to type the key left to your backspace key, then the letter you need.

---

### Post by tacutu on 2010-01-15
It depends on how often you need those accented characters (some methods take longer). There are several methods, as previous answers show:

1. switch keyboard inputs (you can also add a keyboard indicator in the panel)

2. use unicode codes: ctrl+shift+u and type the code

3. Copy-paste from Applications-> accesories-> character map

4. use xmodmap to customize your keyboard layout

edit:
it appears that the German keyboard does have accents and tilde. Try right alt+accent+letter

---


---
title: "[SOLVED] Keyboard mappings and characters..."
date: 2008-11-17
forum: General Help
---

### Post by Jacob Collstrup on 2008-11-17
Heya,

I'm havinga bit of a problem with the keyboard on my laptop. As far as I know pressing [Shift]+[hat] should make a small hat like this: &#7610;, but it doesn't fx if I want to raise something to the power of two (fx 3) then I'd write 3&#7610;2, but what I get is 3², this poses a problem when I'm making scripts and calculations in Matlab, because it doesn't understand '²' it understands '&#7610;2'.

Now I do like that I can type '²' like this, but how can I make it easy to switch between the two?

If I have to make a final decision on one of them, then I'd like to have '&#7610;'. How do I get about that?

Jacob

---

### Post by jesuisbenjamin on 2008-11-17
Hey Jacob,

Shift + ^ returns ^ fine on my keyboard and to return ² i use AltGr + 2. What keyboard layout are you using? You may want to use the US international keyboard (AltGr Dead Keys). I assume you know how to change your keyboard layout, else let me know.

---

### Post by Jacob Collstrup on 2008-11-17
Hmm...I tried to add your keyboard layout to my machine. Pressing [SHIFT]+[^] returns does this: 3² pressing [AltGr]+[^] doesn't return anything.

But I notice that my keyboard model is set to 'Generic 105-key (Intl) PC', I don't think thats correct...its a danish keyboard, it has the 'æ','ø and 'å' characters. And I'm on an IBM Thinkpad R51, I might have the wrong keyboard installed?

Jacob

---

### Post by geirha on 2008-11-17
The caret ^ is often a [dead key](http://en.wikipedia.org/wiki/Dead_key), meaning it waits for another character to "combine" them. For instance Shift+^+e gives ê. To only get the caret, use Shift+^+space.

---

### Post by jesuisbenjamin on 2008-11-17
> **Jacob Collstrup said:**
> Hmm...I tried to add your keyboard layout to my machine. Pressing [SHIFT]+[^] returns does this: 3² pressing [AltGr]+[^] doesn't return anything.

But I notice that my keyboard model is set to 'Generic 105-key (Intl) PC', I don't think thats correct...its a danish keyboard, it has the 'æ','ø and 'å' characters. And I'm on an IBM Thinkpad R51, I might have the wrong keyboard installed?

Jacob

The Keyboard name is Generic 105-key (Intl) PC, which is correct on your laptop -- it should be standard (you can try to count the keys ;) )
The layout you may have however can be changed, a layout tells 'what character is attributed to which key'.
If you check again your System> Preferences> Keyboard and select the 'layout' tab. You may have now two layout listed (since you installed USA international just before).
Now you either want to have the USA International by default or make sure you can switch keyboard as you are using your computer.
If you make the USA international (AltGr Dead Keys) default by ticking Default on the right hand side, and press the 'Apply sytem-wide' button, you can then try it out in the box beneath.
Note:
Depending on which version of Ubuntu you are using, it may respond differently, 8.10 will not ask for a space after ^ to print ^ e.g.:
[LIST]
[*]8.10 If you press Shift + ^ it should return ^
[*]8.04 If you press Shift + ^ you see nothing, press Space and it returns ^
[/LIST]
Now if you want a ², press AltGr+2.
 
Since you need quite a significant amount of æ, å and ø to express yourself in Danish, you may want to know the following keys are available on USA International as:
[LIST]
[*]AltGr + z = æ
[*]AltGr + w = å
[*]AltGr + l = ø
[/LIST]

If you don't want to use USA international continuously but rather switch from Danish Keyboard to USA Int., you can do that again in the Keyboard preferences.
Under layout tab you click Othe options. Under layout switching you can chose the combination of keys you like best to switch from a layout to another. I personally like to use the left Win Key since it is useless with Ubuntu.

If you need more help let me know, i hope this helps though.

---

### Post by jesuisbenjamin on 2008-11-17
> **geirha said:**
> The caret ^ is often a [dead key](http://en.wikipedia.org/wiki/Dead_key), meaning it waits for another character to "combine" them. For instance Shift+^+e gives ê. To only get the caret, use Shift+^+space.

In this case Jacob does not uses the caret as an *accent circonflexe* but as a standalone character.
The former is produced with the AltGr + ^, e combination while the second is produced with Shift + ^.
Besides: some dead keys have been resurrected by 8.10 :)

---

### Post by Jacob Collstrup on 2008-11-17
I think I just screwed up there...:oops:

I totally forgot you had to use the spacebar...now it works as I think it should! Neat! Now I can write both 3^2 and 3²!! :cool: 

Though I haven't figured how to switch keyboard layout. My keyboard doesn't have the [win] key, so according to the keyboard layout I should press both [ALT] keys simultaneously to switch layout, but I can't see anything happening when I do that. I don't think it changes anything...I try pressing both [Alt] keys when I have the keyboard layout open, but nothing happens, neither when I hold the keys down. Is that supposed to happen?

Jacob

---

### Post by jesuisbenjamin on 2008-11-17
> **Jacob Collstrup said:**
> I think I just screwed up there...:oops:

I totally forgot you had to use the spacebar...now it works as I think it should! Neat! Now I can write both 3^2 and 3²!! :cool: 

Though I haven't figured how to switch keyboard layout. My keyboard doesn't have the [win] key, so according to the keyboard layout I should press both [ALT] keys simultaneously to switch layout, but I can't see anything happening when I do that. I don't think it changes anything...I try pressing both [Alt] keys when I have the keyboard layout open, but nothing happens, neither when I hold the keys down. Is that supposed to happen?

Jacob

Jacob,
I'm glad you found your way through all this. As to switch keyboard you don't see much happening on the screen. When you type it should make a difference - especially if you have two strictly different keyboards e.g. Danish and Persian.
Make sure the key combination for switching in the preferences is checked. 
If you want a little help when switching keyboard - that is to see what keyboard you are now using, you can right-click on your panel and add a launcher. Select the Keyboard Indicator.
From now on there is a little flag on your panel, it represents the nationality of your keyboard layout, when you switch layout, the flag should change accordingly.

---

### Post by Shwan.c on 2009-04-26
> **jesuisbenjamin said:**
> Jacob,
I'm glad you found your way through all this. As to switch keyboard you don't see much happening on the screen. When you type it should make a difference - especially if you have two strictly different keyboards e.g. Danish and Persian.
Make sure the key combination for switching in the preferences is checked. 
If you want a little help when switching keyboard - that is to see what keyboard you are now using, you can right-click on your panel and add a launcher. Select the Keyboard Indicator.
From now on there is a little flag on your panel, it represents the nationality of your keyboard layout, when you switch layout, the flag should change accordingly.

I use SweISH keyboard layout and space is not returnming anything, I changed the key layout in system-pref. to elimnate dat keys and now it works fin !

---


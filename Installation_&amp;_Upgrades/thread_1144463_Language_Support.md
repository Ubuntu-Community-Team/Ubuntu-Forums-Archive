---
title: "Language Support"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by boabawhales on 2009-04-30
[FONT=Verdana]I am working with a freshly installed Ubuntu, but I couldn't get language support to work...

When i click on it from the menu it starts to "check available language supports" then it just terminates... without any error messages...

I tried running ```
sudo gnome-language-selector
``` and the same thing happened... and this is the output in the terminal...

```
/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py:837: GtkWarning: gtk_cell_view_set_cell_data: assertion `cell_view->priv->displayed_row != NULL' failed
  cell = combo.get_child().get_cell_renderers()[0]
Traceback (most recent call last):
  File "/usr/bin/gnome-language-selector", line 34, in <module>
    options=options)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 171, in __init__
    self.updateUserDefaultCombo()
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 58, in wrapper
    res = f(*args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 850, in updateUserDefaultCombo
    defaultLangName = self._localeinfo.translate(defaultLangCode)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/LocaleInfo.py", line 148, in translate
    return self.translate_language(locale)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/LocaleInfo.py", line 110, in translate_language
    lang_name = gettext.dgettext('iso_639', self._lang[lang])
KeyError: 'C'
```[/FONT]

---

### Post by zvacet on 2009-04-30
I don´t know if this will help but you can try

```
aptitude search language pack
```

and when you find one you want 

```
sudo apt-get install Package_name
```

---

### Post by boabawhales on 2009-05-01
there are a lot of results from searching "chinese pack"...  i am new to this and don't quite even understand the descriptions...

---

### Post by zvacet on 2009-05-01
```
sudo apt-get install language-pack-zh
```

---

### Post by boabawhales on 2009-05-02
After running

```
sudo apt-get language-pack-zh
```

what do i do?

the whole system is still in english... and the "language support" still crashes...

---

### Post by zvacet on 2009-05-02
You didn´t run right comand,because it is not 

```
sudo apt-get language-pack-zh
```

it is 

```
sudo apt-get install language-pack-zh
```

Try it and see if make any difference.

---

### Post by staar2 on 2009-05-12
Ok i am getting same problem, also my encoding is all wrong
> 
sudo gnome-language-selector
/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py:837: GtkWarning: gtk_cell_view_set_cell_data: assertion `cell_view->priv->displayed_row != NULL' failed
  cell = combo.get_child().get_cell_renderers()[0]
Traceback (most recent call last):
  File "/usr/bin/gnome-language-selector", line 34, in <module>
    options=options)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 171, in __init__
    self.updateUserDefaultCombo()
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 58, in wrapper
    res = f(*args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 850, in updateUserDefaultCombo
    defaultLangName = self._localeinfo.translate(defaultLangCode)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/LocaleInfo.py", line 148, in translate
    return self.translate_language(locale)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/LocaleInfo.py", line 110, in translate_language
    lang_name = gettext.dgettext('iso_639', self._lang[lang])
KeyError: 'C'



---

### Post by Hypo on 2009-05-27
Hello Guys!

I'm a hungarian guy and I'm using ubuntu 8.04.2
My motherkanguage is hungarian, so the default language is the same in the system. I've installed a program, that don't understand my language. So I changed my preferences in System > System Settings > Language support to us english and reboot the system. After grub, before the login screen I've got a small window with a red circle and one and a half rows of small squares, and a little button with two small squares(i think that means OK) So I press the button, and the boot process restarts. What can I do now? I tried to install language packeges, but they don't worked. Now i've tried to run ```
dpkg-reconfigure-locales
```but now i can't work with my computer. 
PLS help me!

THX

---

### Post by tacomodo on 2009-07-05
Any fix for this yet?

My language selector is also crashing with the same errors as here, and I can't use any of the characters from my country in gnome-terminal (øæå), but here in firefox they work fine...

---

### Post by blinkdawg on 2009-07-19
I've got the same problem as the original poster: "[language-selector] [FONT=Verdana]just terminates... without any error messages..."

I tried repairing, and then uninstalling and reinstalling it, but to no avail... :(
[/FONT]

---

### Post by blinkdawg on 2009-07-19
Okay, I tried:
[FONT=Verdana]sudo gnome-language-selector[/FONT][FONT=Verdana]
[/FONT]...and that got me around the problem...but clicking the Language Support icon still doesn't work.

---

### Post by ruPaladin on 2009-07-24
I had the same problem, try this:
Go /etc/apt/ as ROOT and change permission on file sources.list:
For group "Others" change permission to read only.

P. S. Sorry for my English.

---


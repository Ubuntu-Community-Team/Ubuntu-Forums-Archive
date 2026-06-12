---
title: "Keyboard's keys don't work"
date: 2007-07-24
forum: Hardware &amp; Laptops
---

### Post by Hereldar on 2007-07-24
In one of my machines (AMD Athlon(tm) 64 Processor 3200+) I have installed Ubuntu (Gnome 2.18.1/Kernel 2.6.20-16-generic) and Windows XP (SP2). For diverse reasons I have had to reinstalar several times the equipment and GNU/Linux always has detected the keyboard to me to first. The last time that I also installed it was thus but after days to form it to my taste and to install and to desinstall different applications I realized of which some keys had let respond to me, in particular: Super, Alt Gr, ñ, ç, ° and ¿ . As if the keyboard was not formed in Spanish we go. The case is that in xorg.conf the formed keyboard this like Spanish:
[INDENT]Section "InputDevice"
[INDENT]    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "es"[/INDENT]
EndSection[/INDENT]
Following the advice of some friends with more experience than I in GNU/Linux and watching in the forum and different webs have proven several commandos but no she has solved nothing to me:
[INDENT]dpkg-reconfigure xserver-xorg

setxkbmap -layout 'es,es' -model pc105 (It gave back the message "Error loading new keyboard description")

dpkg-reconfigure locales[/INDENT]
In addition it does not seem to be thing of Gnome because I installed KDE to prove it and also it gave he himself problem me and in Windows it continues working well so I do not believe that it is thing of the keyboard. Definitively I do not have nor idea that it is what happens to him to my keyboard and I almost am in favor of reinstalar Ubuntu but I have curiosity to know that is what happens and annoys to me to have to return to form it everything.

Thanks to have had the patience to read all this roll, I feel that my English is so bad.

---

### Post by Hereldar on 2007-07-30
Anyone can help me?

---

### Post by misty soul on 2007-07-30
Does your keyboard work correctly when you are on a text-only console ?
To check this, do the following :

1) switch to a text-only console by pressing keys Ctrl-Alt-F1 (the control and Alt modifier keys and the F1 function key all at the same time)
   you should see the graphical display be replaced by a black screen with a text-only login prompt

2) log on the text-only console (type username and password as usual)

3) check if the keyboard work in this very basic mode

4) log out of the graphical console by issuing the command "exit"

5) go back to the graphical display by pressing Alt-F9 (or Alt-F8 or some other number, it may depend on your system, just try several keys until you go back to graphical display)

If the keyboard works correctly on the text-only console and not on the graphical display, then the problem is related to X configuration (/etc/X11/xorg.conf). If the keyboard does not work on the text-only console, then the problem is at very low level and you should look at /etc/default/console-setup.

---

### Post by Hereldar on 2007-07-31
Ctrl-Alt-F1 don't work in my computer, but I initiated a console session and the error followed there.

/etc/default/console-setup:

# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.
XKBMODEL="pc105"
XKBLAYOUT="es"
XKBVARIANT=""
XKBOPTIONS=""

---

### Post by misty soul on 2007-07-31
It seems to me the configuration files for both console and X are good and refer to the spanish layout, but when the sytem tries to set this configuration up it fails to find this layout. Here are a few random thoughts, not related to each other.

Do you have the console-setup package completely installed ?

Could you try to install console-data and console-common  and look at what is there ?

Did you look at the loadkeys/dumpeys/showkey/keymaps manual page ? This could help you find first what you current layout is and second what you could do to modify it.

Did you also try to reset the keyboard directly from the Gnome menu (System->Preferences->Keyboard and using the layout tab) ?

---

### Post by Hereldar on 2007-08-01
Thanks, but there is no way of which the keyboard works.

1 - Console-setup: reinstalled,

2 - Console-data and console common: installed.

3 - loadkeys/dumpeys/showkey/keymaps: ?

4 - Gnome menu: error:

[INDENT]Error al activar la configuración XKB.
Podría deberse a varias circunstancias:
- un fallo en la biblioteca libxklavier.
- un fallo en el servidor X (utilidades xkbcomp, xmodmap)
- Un servidor X con una implementación incompatible con libxkbfile

Datos de la versión del servidor X:
The X.Org Foundation
70200000

Si informa de esta situación como un fallo, por favor incluya:
- El resultado de xprop -root | grep XKB
- El resultado de  gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

-----

xprop -root | grep XKB:
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "es", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "es", "", ""

gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd:
 layouts = [es,es]
 model = 
 options = [grp grp:alts_toggle]
 overrideSettings = true

libxklavier, xkbcomp, xmodmap and libxkbfile: reinstalled[/INDENT]

---

### Post by misty soul on 2007-08-01
Your setup seems to be really broken. Everything on the configuration file side seems OK to me (xprop, gconftool), and all applications seems OK since you have reinstalled all required core packages. You are not in a classical situation: something (probably a low level setting) has been changed and we should find what.

I think there is some problem with you low level keyboard handling, which is managed by loadkeys and friends. These utilities are used very early at boot time to configure the kernel. Perhaps the X configuration inherits some of these settings too.

I would try to first make the keyboard work at low level on the text-only consoles before trying the graphical display. This implies booting in a text session (since Ctrl-Alt-F1 does not work for you) an
d using the low level tools. Loadkeys is used to set up the key map (i.e. which code corresponds to which character). Dumpeys does the opposite: display the current map. Showkey display the code for one key at a time, when you press it. Keymaps is the format of the key map files.

You could save the output of dumpkeys to find what is your current setting. This should show what you really can type, but you should notice no keys are associated with the specific spanish characters you miss. You can search on the web if some similar file is available on the internet with ALL the keys you want and use it as an argument to loadkeys in the boot scripts. If you don't find any hint, you can try to build such a file yourself by editing the current file and adding the codes of the missing characters. The showkey utility may be useful here. You can run it and press the keys you want and notice the corresponding code. Once you know the code you simply add the association code<->character in the file and use loadkeys to reload this file. You can get documentation about these utilities and formats by reading the manual pages. Just type "man loadkeys" or "man keymaps" or similar in a console window to read it.

I'm sure there is an easier way to fix your system, but I don't understand what is broken, so I can't provide any hints to you. This is really weird.

I'm sorry not to be able to help you more

---

### Post by Hereldar on 2007-08-01
Thank you very much, I will reinstall then Linux, in any case I have learned much trying to fix this keyboard, has been a pleasure.

---


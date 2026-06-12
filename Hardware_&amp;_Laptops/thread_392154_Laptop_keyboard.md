---
title: "Laptop keyboard"
date: 2007-03-24
forum: Hardware &amp; Laptops
---

### Post by Laki on 2007-03-24
Hello!

I have [Clevo D410S laptop ]("http://www.clevo.com.tw/products/D410S.asp"), with dualboot Ubuntu 6.06 Dapper Drake / Win XP.

When I installed Ubuntu keyboard output was fine ( I use Slovene output). Then I tryed some live linux distros, and one of them haven't had correct keyboard to select, and I selected some other ( I don't remember wich). After that I have messed up laptop keyboard layout. I think that live distro somehow changed keyboard mapping settings or something like that. 

My xorg.conf has:
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"si"
EndSection

and in System -> Settings -> keyboard -> Layouts, I have keyboard model 105 key (intl) PC, with Slovene selected layout.

I'm typing this with additional standard 105 key keyboard. Keyboard doesn't work right in XP too. How can I reconfigure my keyboard to the right one, my laptop has?

---


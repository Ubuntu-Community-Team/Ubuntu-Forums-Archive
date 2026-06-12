---
title: "keyboard Preferences"
date: 2009-01-21
forum: Hardware
---

### Post by jiangshi on 2009-01-21
Ubuntu has under System/Preferences a listing named Keyboard. Selecting this gives the user many options for the keyboard, all in a dialog box titled "Keyboard Preferences. One of the main options is having more than one keyboard layout available. This is especially handy for using the standard US English keyboard layout for normal typing, and having a second keyboard layout for a different language. For example, I use a layout for typing pinyin in SCIM and it produces Simplified Chinese characters.

This "Keyboard" menu option seems to be missing from Xubuntu menus, which in itself seems odd since Ubuntu is dedicated to supporting many languages. I would greatly appreciate any help in knowing what package(s) I might need to load in order to get the same functionality in Xubuntu.

Thank you!

~jiangshi

---

### Post by jiangshi on 2009-01-21
Okay, I have found a solution. Don't know if it is the best, but it seems to work.

In prowling around on the Xubuntu site, I found a document entry for 6.06, but it works for 8.10. It seems there is no graphical interface for setting up the switching between two or more keyboard layouts in Xubuntu. However, the document entry showed what needed to be added to the appropriate configuration file. I will repeat that information here.

Basic Process of adding an additional keyboard layout.

1. Start the file browser (Thunar) at the system level
2. Navigate to /ETC/X11
3. You should see a file named "xorg.conf"
4. Right-click in an empty space
5. From the right-click menu, choose "Open Terminal Here" Note: I sure wish Nautilus had this option.
6. In the terminal window type the following: sudo gedit xorg.conf
Note: I use Gedit, however, you may use whatever text editor you like. Gedit is not loaded in Xubuntu by default, but do an "sudo apt-get install gedit" to get it and install it on your system. It's a great gui text editor
7. Press the Enter key. You will be prompted for your sudo password
8. After entering your sudo password, whatever edit you typed in the commandline will start with xorg.conf file loaded.
9. Go to the bottom of the file and add the following text:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us,gb"
EndSection

10. Note the line containing "XkbLayout" and "us,gb". This example uses the standard US keyboard and the Great Britain keyboard. I use the gb keyboard because I have modified the key layout file to be able to type pinyin with tone symbols. How to do all of this is detailed elsewhere on the Ubuntu site. The point is that you can add whatever keyboard layout(s) you want. Just make sure to separate them with a comma.

11. Save the xorg.conf file after making your changes. Note: since this is a system file, you should make a backup of the original before modifying it.

12. At the commandline prompt type:  setxkbmap us,gb
Note: make sure to change the "us,gb" to whatever keyboard layouts you are using

12. Close the terminal session
13. Right-click on the top panel on your desktop
14. Select Add New Item
15. From the list, select "Keyboard Layout Switcher"

Note: you may have to log out and log back in again or even rebootfor the changes to take effect.

Your Xubuntu system is now ready for using two or more keyboard layouts. To change layouts, simply click the icon on the top panel, and start typing in your favorite word processor or text editor.

~jiangshi

---


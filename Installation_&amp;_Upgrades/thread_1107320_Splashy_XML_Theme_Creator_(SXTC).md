---
title: "Splashy XML Theme Creator (SXTC)"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by schmidtbag on 2009-03-26
[SIZE="5"][ATTACH]107703[/ATTACH][/SIZE]

What is Splashy:
Splashy is a lightweight but customizable boot screen program.


What is SXTC:
SXTC is a shell script I wrote that automatically creates and writes the XML files used by Splashy themes and places all files where they need to be, so all you have to do is find out the information it asks you (such as the dimensions of the progress bar or colors)


Using SXTC:
To execute this, move to the current directory in Terminal and type "./sxtc.sh".  If that doesn't work, be sure to make sxtc.sh and sdf-xml.sh to have executable permissions by you.  Do not run anything else, as you will get errors and random temporary files.

If you want to test the pre-made theme (Splashy's default), copy the "default" folder to /etc/splashy/themes/ and merge the old one.  If you decide to stop using this program, it will not affect the current theme.  Do NOT move the default.xml, the program does rely on that script.


FAQs:
Q: What is the resolution and color depth limit?
A: You should use 800x600 and 16-bit colors but I'm not entirely sure if its limited to that.
Q: Is this KDE or XfcE compatible?
A: This is a standard shell script so most of it should work.  It installs everything it needs for a GNOME desktop but you may want to change programs such as gnome-terminal to your default terminal.
Q: Can this open any Splashy theme?
A: No, this will only open themes that this program created.  If you decide to open a non-SXTC edited program and save the changed data it WILL overwrite the current setup.
Q: Can this work with uSplash themes?
A: No, those are completely incompatible.


Questions?  Comments?  Suggestions?  E-mail me at [email]zicronsoft@yahoo.com[/email]


Please help promote this as much as you can.

---


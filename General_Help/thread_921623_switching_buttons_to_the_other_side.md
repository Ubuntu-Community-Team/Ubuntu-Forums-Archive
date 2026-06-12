---
title: "switching buttons to the other side"
date: 2008-09-16
forum: General Help
---

### Post by robcalewar on 2008-09-16
I installed mac4lin RC 1.0 and I want to change the close/minimize/maximize buttons to the right again. How do I do this? I changed the theme and it just applied the theme correctly however the buttons are still on the left

[[IMG]http://img384.imageshack.us/img384/2180/screenshotue3.th.png[/IMG]](http://img384.imageshack.us/img384/2180/screenshotue3.png)

---

### Post by DJ_Peng on 2008-09-16
The answer in the older (v 0.4) [documentation]("http://sourceforge.net/project/showfiles.php?group_id=204373&package_id=243878"), but it's a little hard to find on the site. It took me some diffing to get the link. Anyway, on page 6 of the PDF is this:

> The following is only for those who do not use Emerald Themer, used in conjunction with Compiz/Fusion/Beryl (if you do not about Emerald/Compiz etc. refer to Page 9, Section 3):

To shift the traffic lights (close, min, max buttons) to the left of the title bar goto a terminal window/press Alt+F2 and type: “gconf-editor” and press Enter. Now navigate to: apps>metacity>general. On the right double click “button_layout”. Delete that & type: “close,minimize,maxmize:menu” (without quotes). Press OK and then Quit. The buttons will now be on the left side of titlebar. To restore the original layout, just replace the string by “menu:minimize,maximize,close”If the window decoration is handled by Emerald, you'll need to go into the Emerald Theme Manager. Select the theme in the Theme Settings tab and then go to the Edit Themes tab. Go over to the Titlebar tab and change the Title-bar Object Layout and change it to> HM:(5)T:C(5)N(5)XIf you want to include the icon on the titlebar change it to
> HM:I(5)T:C(5)N(5)XI think it may be a typo in the 1.0 Emerald theme that there's no icon on the titlebar, but that should switch things back over for you.

---


---
title: "Ubuntu 16.04: Which Nvidia graphics drivers to use (not nouveau)?"
date: 2017-09-15
forum: Hardware
---

### Post by mrjayviper on 2017-09-15
[COLOR=#141414][FONT=arial]So I want to install the proprietary drivers for my GTX770 and I found conflicting information.[/FONT][/COLOR]

[COLOR=#141414][FONT=arial]I found this ([/FONT][/COLOR][https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu_14.04_and_up](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu_14.04_and_up)[COLOR=#141414][FONT=arial]) official Ubuntu page and it seems to me it uses Nvidia drivers that are provided by Ubuntu. I'm guessing I don't need to add additional entry on my repository list to access this.[/FONT][/COLOR]

[COLOR=#141414][FONT=arial]But I also found this PPA ([/FONT][/COLOR][https://launchpad.net/~graphics-drivers](https://launchpad.net/~graphics-drivers)[COLOR=#141414][FONT=arial]). Multiple internet guides suggests this 3rd-party repository for Nvidia drivers.[/FONT][/COLOR]

_So which one to use?_

[COLOR=#141414][FONT=arial]Also Is there some sort of alias to install the latest so I don't have to know which version number to use?[/FONT][/COLOR]

[COLOR=#141414][FONT=arial]example:[/FONT][/COLOR]

[COLOR=#141414][FONT=arial]use[/FONT][/COLOR]
[COLOR=#141414][FONT=arial]```
sudo apt-get install nvidia-latest
```[/FONT][/COLOR]

[COLOR=#141414][FONT=arial]instead of[/FONT][/COLOR]
[COLOR=#141414][FONT=arial]```
sudo apt-get install nvidia-375
```[/FONT][/COLOR]

[COLOR=#141414][FONT=arial]I tried:[/FONT][/COLOR]

[COLOR=#141414][FONT=arial]```
sudo apt-get install nvidia-current
```[/FONT][/COLOR]

[COLOR=#141414][FONT=arial]and it wants to install version 30x which I know is definitely not the latest.[/FONT][/COLOR]

[COLOR=#141414][FONT=arial]Thanks for the help.[/FONT][/COLOR]

---

### Post by Autodave on 2017-09-15
The safest way is to go into your *Settings.* Once in that, go to *Additional Drivers* and let Ubuntu search for the latest driver. Once found, allow it to install.

---


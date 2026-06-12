---
title: "Trying to temporarily disable touchscreen, names in xinput too generic"
date: 2018-03-07
forum: Hardware
---

### Post by reddeth2 on 2018-03-07
Hi everyone, not even sure if this technically needs to be in Desktop Environments, Hardware, etc, but I hope I can start here.

I have a Dell XPS 13 Developer Edition (9370) running Ubuntu 17.10 with Gnome 3.26.2. 

I'd like to be able to use this Gnome extension: [https://extensions.gnome.org/extension/991/toggle-touchscreen/]("https://github.com/mkopta/toggle-touchscreen")

It installs fine, and shows up in Gnome okay, but clicking it does absolutely nothing.

I've run the looking-glass debug tool, the extension is installed and throws no errors:

[IMG]https://i.imgur.com/vJlpBlN.png[/IMG]

Looking at the source code for the extension I find this line: [https://github.com/mkopta/toggle-touchscreen/blob/master/extension.js#L30](https://github.com/mkopta/toggle-touchscreen/blob/master/extension.js#L30)

Which shows that the plugin is running xinput and looking for touchscreen on each line. However, when I run xinput myself, I do not see any device labelled touchscreen:

[IMG]https://i.imgur.com/z97dYds.png[/IMG]

So my question ultimately is: Is the plugin wrong? Or is xinput wrong? (And when I say wrong, I mean is something I did incorrect - not blaming the system or the plugin) How can I get this to work? I know there's plenty of solutions to disable the touchscreen entirely, but I'd really like to be able to temporarily disable it.

Thanks for the help!

---


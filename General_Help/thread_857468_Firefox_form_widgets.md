---
title: "Firefox form widgets"
date: 2008-07-12
forum: General Help
---

### Post by airbornemist6 on 2008-07-12
I'm tired of how ugly the firefox form widgets are under gtk 2.0. Honestly, I've stopped using Linux for browsing because I HATE how ridiculously bad FF3.0 is with dealing with the widgets. They have that ugly border around them, and it makes them painful on my eyes. Has anyone figured out how to deal with this yet?

Here's an example, look at my attached screenshot, check out the address and search bar, that's what I'm talking about. I'm currently using a gtk theme that was designed with dealing with this in mind, but I think it's about time we got this fixed. Honestly, windows xp looks better than this, and it's already 6 years old.

---

### Post by joshdudeha on 2008-07-12
Mine doesn't look like that.
But I do agree with it looking a bit naff.
I mean, they've carefully designed it in Vista, xp and mac - giving it nice buttons and stuff, but we're left with Tango, which in my opinion is very pretty.

:/

---

### Post by airbornemist6 on 2008-07-12
I don't know why it's doing it. It does it on my desktop install too. I know there's been reported problems on webpages, which I also have, but I'm not sure why the awesome bar and search bar have problems.

---

### Post by airbornemist6 on 2008-07-13
insert shameless bump here

---

### Post by spupy on 2008-07-14
The problem is located in Firefox and the theme engine you are using. Firefox uses gtk widgets. When a gtk widget (a button, for example) is used in a gtk program, the background of the button is the color of the parrent widget. So buttons in gtk program have no ugly gray box around them and blend with the rest of the window. 
They way firefox uses the gtk widgets, they have no way to get the color of their parrent widget, and they end up with a default gray.
The solution would be a theme engine which draws widgets with a transparent background around them, rather than a colored rectangle. 
For now, the only solution is to use a rectangular theme. :(

---

### Post by airbornemist6 on 2008-07-14
God, I was afraid you were going to say that. I had a bad feeling that's what it was. But I wasn't sure, unfortunately, now I am. Oh well thanks anyway.

---

### Post by DaymItzJack on 2008-07-14
[http://ubuntuforums.org/showthread.php?t=369596](http://ubuntuforums.org/showthread.php?t=369596)

Did you even try that?

---

### Post by airbornemist6 on 2008-07-14
Yeah, unfortunately, it broke firefox personas and now I can't update to the newest version. But it made no difference whatsoever.

---

### Post by spupy on 2008-07-14
> **airbornemist6 said:**
> God, I was afraid you were going to say that. I had a bad feeling that's what it was. But I wasn't sure, unfortunately, now I am. Oh well thanks anyway.

Look at your screenshot - the address bar. The left side has the ugly gray, but the right side doesn't. It is the same with the aurora engine. I was using it when i noticed. Some of the widgets do use transparent background, some don't. I looked at the source of Aurora, but I don't know gtk nor c. Besides, it isn't feasible to change all theme engines just for firefox.

---

### Post by airbornemist6 on 2008-07-14
I think it's actually a bigger deal than it seems. Honestly, when I'm trying to get people to switch to ubuntu from windows or osx, my biggest appeal is the eyecandy appeal.

---


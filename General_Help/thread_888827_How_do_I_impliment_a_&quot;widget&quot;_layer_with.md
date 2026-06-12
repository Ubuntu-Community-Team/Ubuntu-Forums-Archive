---
title: "How do I impliment a &quot;widget&quot; layer with a hotkey?"
date: 2008-08-13
forum: General Help
---

### Post by diablo75 on 2008-08-13
I've not had luck with getting a widget layer going with compiz in the past.  I must have been doing something wrong.  I have a friend who wants to try Ubuntu, and is asking for some features I've never really tried to do with compiz before.  He wants there to be a widget layer of some kind, just like you have in Mac OSX, where you press a hotkey and in flys all the widgets.  Hit it again, they fly away.  How can this be done in Ubuntu?

---

### Post by DaymItzJack on 2008-08-13
ccsm -> Widget Layer plugin -> Toggle Widget display -> F9 or something.

Then go to the Behavior tab and hit the "+" button and select the type/name of the window you want, that window will go away and when you press F9 it will show up.

---

### Post by diablo75 on 2008-08-13
Sweet!  Thanks a lot!

---

### Post by diablo75 on 2008-08-13
I'm having a little bit of trouble.

I'm using Screenlets for the stuff I want on the widget layer.  I'm just guessing that's how ya do it... I don't know.  Never done this before.

Anyway, when I open up ccsm and go to the behavior tab you described, click add, then the "grab" button to turn the mouse into a + and then click on the screenlet... that works for one screenlet.  But when I add a second one, it doesn't seem to do the trick right.  Like it's not adding the screenlet it that I want, if not making the first screenlet fail to toggle like it did when you hit F9.

I've noticed the syntax it is putting in appears a bit different.  One command (looks like a python script is being called) is placed inside of parenthesis, the next is not, and they are separated by an & symbol.  I tried removing the parentheses but that didn't seem to help...  I might add some to the second command and see what happens.

What am I doing wrong?  Does it have to do with the window type I have selected?  "Class"?  I'm not sure.  Please help!

:)

---

### Post by conundrumx on 2008-08-13
If you right click on a screenlet it has a a checkbox under "Window" titled "Widget".  This will automatically put that sceenlet on the Widget layer under Compiz.

---

### Post by DaymItzJack on 2008-08-13
> **diablo75 said:**
> I'm having a little bit of trouble.

I'm using Screenlets for the stuff I want on the widget layer.  I'm just guessing that's how ya do it... I don't know.  Never done this before.

Anyway, when I open up ccsm and go to the behavior tab you described, click add, then the "grab" button to turn the mouse into a + and then click on the screenlet... that works for one screenlet.  But when I add a second one, it doesn't seem to do the trick right.  Like it's not adding the screenlet it that I want, if not making the first screenlet fail to toggle like it did when you hit F9.

I've noticed the syntax it is putting in appears a bit different.  One command (looks like a python script is being called) is placed inside of parenthesis, the next is not, and they are separated by an & symbol.  I tried removing the parentheses but that didn't seem to help...  I might add some to the second command and see what happens.

What am I doing wrong?  Does it have to do with the window type I have selected?  "Class"?  I'm not sure.  Please help!

:)

Make sure you're using the "or" relation and not the "and" relation. As for screenlets though, you should just use the built in option as explained by conundrumx.

---

### Post by diablo75 on 2008-08-14
> **conundrumx said:**
> If you right click on a screenlet it has a a checkbox under "Window" titled "Widget".  This will automatically put that sceenlet on the Widget layer under Compiz.

Ok, this did exactly what I was looking for!  Awesome.  Thank you very much!
:guitar:

---


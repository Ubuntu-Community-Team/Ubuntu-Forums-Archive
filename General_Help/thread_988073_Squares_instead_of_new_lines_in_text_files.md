---
title: "Squares instead of new lines in text files"
date: 2008-11-20
forum: General Help
---

### Post by Daminator on 2008-11-20
Hello all,

I use txt files quite quite a lot and share them between Windows and Ubuntu.

I notice quite a lot that if a text files has been edited in Ubuntu (using gedit), when I look at it again in Windows there are small squares in the text in all the places where a new line should be (enter/return has been pressed).

Can anyone explain why this happens and is there a solution to it?

Thanks
Damian

---

### Post by rampageoberon on 2008-11-20
not entirely sure but it could be the unix vs dos format problems.

```
sudo aptitude install tofrodos
unixtodos file
```

maybe the above code will help. worth a shot (try it on a copy of the file first)

hope this fixes things

---

### Post by wylfing on 2008-11-20
One reason you get "disagreements" between Linux and Windows about what the end of text lines should look like is that Linux follows the Unix-like way of ending lines, and Windows...well, Windows of course does its own thing. Running a conversion utility can help you in this regard.

There may also be text-encoding issues as well, I can't remember. One major thing you can do is stop using junky editors like Notepad on the Windows side of things. Get metapad or notepad+ and your problems may disappear.

---

### Post by snova on 2008-11-20
Unix-based systems (including Ubuntu) have always used the '\n' character to represent line endings. Windows uses '\r\n'. Since it doesn't find this pattern but instead finds a character with no representation, you get a box.

This has less to do with Ubuntu and more to do with Notepad not being able to handle it. Better editors can.

---

### Post by Daminator on 2008-11-21
Great, thanks for that.

I'll try leaving everything as it is and just installing a better notepad prog in windows.

Any recommendations for the lightest smallest free replacement that will work?

---

### Post by wylfing on 2008-11-21
I would turn first to the fantastic [Notepad++]("http://notepad-plus.sourceforge.net/uk/site.htm").

If for some reason that doesn't do it for you, try [Metapad]("http://www.liquidninja.com/metapad/").

---

### Post by Daminator on 2008-11-24
Great, thanks

---


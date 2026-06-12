---
title: "New to linux (Terminal question)"
date: 2008-10-10
forum: General Help
---

### Post by lilsancho on 2008-10-10
Hi everyone, 

just a quick and easy question.

is it possable to write a script/text document (or something) so i can run commands in terminal window (save me typing them all the time) does this make sence?

if it does can anyone give me some advice on how go about doing it? or a web address with information??

Thanks :)

---

### Post by bachya on 2008-10-10
Do you mean shortening commands?  Or actually writing scripts?  They are two different things; for the first one, I'd look at aliases ([http://linuxreviews.org/quicktips/alias/](http://linuxreviews.org/quicktips/alias/)).  For actual scripting, bash is the way to go ([http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/](http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/)).

Let us know if that's what you're looking for.

---

### Post by WWSmith36 on 2008-10-10
This is very basic information for creating a script.  Other people I´m sure can provide more information regarding the content of scripts.

You can write a script in a text editor like gedit.  After you save the file. You can right click on it, select properties, go to permissions tab and tick the box ´Allow executing file as program´.

Now when you open the file you will get a dialog, where you will have choices.

Run in Terminal
Display
Cancel
Run

Hope this helps

---

### Post by hyper_ch on 2008-10-10
if you want to learn more on bash scripting, have a look here:

[http://www.linuxcommand.org](http://www.linuxcommand.org)

---

### Post by lilsancho on 2008-10-10
Thanks everyone, 

your replies have been very useful. it looks like i have a bit  of reading to do lol :)

---

### Post by hyper_ch on 2008-10-10
No need to do all the reading... I rather use a "learn-when-you-require-something" approach.. meaning I just look up if I need to get something done... I'm not reading all that stuff on my one but you should have the basic concepts on how to do loops, how to operate with variables, ...

---

### Post by KeyserSoze93 on 2008-10-10
the easiest approach:

write a load a commands in a file (assuming you know what you want to do), one to each line.

save it as whatever.sh

open a terminal and type ```
bash whatever.sh
```

you can learn about flow control, passing arguments and conditional statements etc. later on, when you're ready.

---

### Post by hyper_ch on 2008-10-10
actually, if you want to use bash as interpreter you'll make your first line as
```

#!/bin/bash

```
and just run it as sh script.sh  or ./script.sh

---


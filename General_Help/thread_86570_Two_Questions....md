---
title: "Two Questions..."
date: 2005-11-05
forum: General Help
---

### Post by PhantomOSX on 2005-11-05
Sorry if these solutions were posted before, and I am new at Ubuntu, so...

1. How do I set Opera as my default browser.

2. I've installed my HP printer now how do I put hp-toolbox in the accessories menu rather than having to keep running it in the terminal.  

I hope I'm not too vague on my questions, it's been a long day.  lol  

Thanks in advance.  :smile:

---

### Post by mustang on 2005-11-05
1. I'm not on Ubuntu right now but if I recall correctly, go to System->Preferences->Preferred Applications (or something along those lines)

I believe there's a tab for the browser. Just put in the command to open opera in there.

---

### Post by Joe_lurker on 2005-11-05
You can add the command to the applications menu using Applications | System Tools | Applications Menu Editor.  I like to add a new menu item called "Joe's Apps" then add all my special programs there.

To do that click on the "New Menu" button.  Enter the information, choose an icon and click Ok.  Highlght the newly created menu in the left pane and choose click on the "New Entry" undder the right pane.  Enter the name of the app (HP Toolbox) and the command of the app (/usr/bin/hp-toolbox).  Choose an icon and away we go!

-Joe

---

### Post by PhantomOSX on 2005-11-05
Ah thanks Joe, it worked perfect.  

Do I put /usr/bin/opera for the command in PA for Opera?  If so everytime I click on a link Opera comes up but doesn't display the page.  :/

---

### Post by Moonbuzz on 2005-11-05
Just looked at my preferred Application, try this ```
opera -newpage "%s"
```

---

### Post by PhantomOSX on 2005-11-05
That seems to have done the trick.  Thanks for your help everyone.  :D

---


---
title: "[SOLVED] How to exit from an error log"
date: 2008-07-20
forum: General Help
---

### Post by PierreQuebec on 2008-07-20
Hello all,

Not sure I'm posting this to the right forum but anyway. I've checked here and there and couldn't find an answer.

I'm installing some package through the Terminal, and it tells me there is an error, after which it asks me if I want to see the log. When I answer that I do, it shows me the error log in the terminal window, but I don't know ***how do I get out of there?*** I tried CTRL-X, CTRL-C, nothing works! :( The only thing that somehow does, is CTRL-Z, but then it puts the error log in the background and doesn't really quit it...

How do I do that?

Thanks
Pierre

---

### Post by scragar on 2008-07-20
**q** is normaly used to **q**uit things like that, with **escape** being a good possibiliy as well.

---

### Post by mbeach on 2008-07-20
depending on the editor it is using to show the error, there might be a few different things to try.

I suspect its vi because of the behaviour of CTRL-Z 
while viewing the file, hit escape then type
:q!
(include the colon) 
this tells vi to quit without saving any changes.

I think issuing the 'fg' command will terminate that vi session after a ctrl-z

good luck,
mb.

---

### Post by PierreQuebec on 2008-07-20
AH! Indeed, "Q" solved it. I was trying CTRL-Q or any other CTRL-something...

Thanks! :) SOLVED! :)

---


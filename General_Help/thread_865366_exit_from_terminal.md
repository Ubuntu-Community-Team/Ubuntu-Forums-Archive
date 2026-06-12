---
title: "exit from terminal"
date: 2008-07-20
forum: General Help
---

### Post by cpetercarter on 2008-07-20
Normally, if i type "exit" into the terminal, the terminal closes. But sometimes, it just echoes "exit" and I have to click on the close button to close the terminal. Why?

---

### Post by louieb on 2008-07-20
Certain commands like su open up a 2nd instance of the shell. Typing exit once closes the 2nd shell. and echoes exit. In this case tying exit again will close the 1st shell and the terminal window.

---


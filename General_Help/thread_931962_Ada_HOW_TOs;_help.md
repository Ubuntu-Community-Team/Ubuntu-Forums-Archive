---
title: "Ada: HOW TOs; help"
date: 2008-09-27
forum: General Help
---

### Post by Stargazer989 on 2008-09-27
i've been reading a wikibook on Ada scripting... but it doesn't tell me how to actually run the program. any ideas ? (google proved useless in this situation).

---

### Post by nsche on 2008-09-27
> **Stargazer989 said:**
> i've been reading a wikibook on Ada scripting... but it doesn't tell me how to actually run the program. any ideas ? (google proved useless in this situation).
Are you talking about programming in the Ada language?  If so you first need to compile and link your program and then run it.  The development/compile environment for Ada is called gnat.  Find that and install it then compile your program and you should be ready to go.

---

### Post by Stargazer989 on 2008-09-27
yeah... i have all that setup; gnat and it's dependencies. what people weren't telling me is how to run the program... i figured it out: ./filename

thanks anways. :)

i may be asking more questions here at a later time.

---

### Post by nsche on 2008-09-28
I worked with Ada for a number of years.  I may be able to help you but then who knows.  The ./filename is how any program which is not on your $PATH is executed.  You have to fully identify it because . is unually not on your $PATH for security reasons (though many change that).

Norm

---


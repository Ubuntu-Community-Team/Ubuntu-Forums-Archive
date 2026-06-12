---
title: "Serial port question"
date: 2008-11-08
forum: General Help
---

### Post by LordVeovis on 2008-11-08
I have a scale that is connected to my pc that I have some software on that will get the weight from the scale.  The software expects the data to be sent like "0XX.XX" where X=numbers and the scale sends the data as "0XX.XXLB" where X=numbers as it should be but LB is added to signify pounds.  Is there any way to prevent that from getting passed to the software as that causes the software to error out?

I knowsome about linux, probably just enough to get myself into trouble.  I know of a few programs like minicom and microcom and the like.  I knowI can take the incoming data and through redirects pass it through sed and have it formatted like i need, but I wouldn't know how to send it to the program.  I had then thought maybe I can emulate a com port and pass the data through to it... but this seems really complicated to do what I am trying to do, nor do I know if it is even possible.

Any help / ideas much appriciated.

---


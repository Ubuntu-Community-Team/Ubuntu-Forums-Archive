---
title: "Verizon USB 760 drops connection?"
date: 2009-09-13
forum: Hardware
---

### Post by POMPEII on 2009-09-13
Need help. Got the Verizon USB 760 working by

  	 	 	 	 	 	   sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
find the line that contains "Novatel_Mass_Storage" and append the following to it:
RUN+="/usr/bin/eject %k"


BUT:  IT DROPS THE CONNECTION EVERY COUPLE OF MINUTES IF THERE IS NO ACTIVITY. SOMETIMES AFTER A FEW SECONDS. IT'S GREAT THAT IT CONNECTS, BUT I'VE HEARD THAT OTHERS ARE HAVING THE SAME PROBLEM WITH NO SOLUTION. 
ANYBODY FOUND A SOLUTION?



THE UM 175 I USED TO HAVE WORKS RIGHT OUT OF THE BOX NO TWEAKING OR DROPPED CONNECTION. SO IF ANYONE NEEDS A VERIZON THAT WORKS GO WITH UM 175.

---


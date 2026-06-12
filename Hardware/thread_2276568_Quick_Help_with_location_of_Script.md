---
title: "Quick Help with location of Script"
date: 2015-05-03
forum: Hardware
---

### Post by neu5eeCh on 2015-05-03
Just purchased a Yoga 2. At [Linlap]("http://www.linlap.com/lenovo_ideapad_yoga_2_pro"), a solution is offered when Suspend resumes if the laptop lid is closed:

> [h=3]Resume immediately after Suspend[/h]    If there is a problem with the laptop waking up after you close the lid this script may help: 


   #!/bin/bash  
echo XHC > /proc/acpi/wakeup
echo EHC1 > /proc/acpi/wakeup 

   
The theory here is that there is some activity (WiFi, maybe) that is  causing the wakeup.  This problem only occurs on lid close, not on  suspend via direct command. 

  


Can anyone tell me where this script should be placed (/bin/bash (?)) and what I should call it? Thanks!

---

### Post by neu5eeCh on 2015-05-03
Okay, more Googling managed to solve this. The two lines are to be added to /etc/rc.local. How hard is it for a blog to add this little detail, I ask you. :-/

---


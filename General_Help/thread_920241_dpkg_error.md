---
title: "dpkg error"
date: 2008-09-15
forum: General Help
---

### Post by eclipsedbymoon on 2008-09-15
Hi all, 
i am new in Ubuntu Hardy Haron. I have a problem to installing new software. When I write "sudo apt-get install vlc" in the terminal, It shows me error "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. " . I am just wondering why this warning shows. I have installed many software using this command. Now what happend? The warning shows since yesterday. Does anyone know the solution. Please?

---

### Post by iaculallad on 2008-09-15
> **eclipsedbymoon said:**
> Hi all, 
i am new in Ubuntu Hardy Haron. I have a problem to installing new software. When I write "sudo apt-get install vlc" in the terminal, It shows me error "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. " . I am just wondering why this warning shows. I have installed many software using this command. Now what happend? The warning shows since yesterday. Does anyone know the solution. Please?

Do as the message say, input the command on the terminal, only this time, add sudo before your command:

```
sudo dpkg --configure -a
```

This correct mostly errors from previous installations.

---

### Post by NoReflex on 2008-09-15
Hello!

Well obviously you can't find the problem without checking some logs. Anyway you can try the suggested solution : 
```
sudo dpkg --configure -a
``` to see if it helps.

Best wishes,
NoReflex

---

### Post by frankleeee on 2008-09-15
> **eclipsedbymoon said:**
> Hi all, 
i am new in Ubuntu Hardy Haron. I have a problem to installing new software. When I write "sudo apt-get install vlc" in the terminal, It shows me error "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. " . I am just wondering why this warning shows. I have installed many software using this command. Now what happend? The warning shows since yesterday. Does anyone know the solution. Please?

In the terminal sudo dpkg --configure -a  it will then ask for your password which wont show hit enter.

---


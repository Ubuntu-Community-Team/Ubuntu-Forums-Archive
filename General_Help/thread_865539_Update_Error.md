---
title: "Update Error"
date: 2008-07-20
forum: General Help
---

### Post by ~Nightingale~ on 2008-07-20
I was trying to update my Flash Player edition, (this is unrelated, just background.) The thing I got off the Flash Player site was not working so i turned to the synaptic. I went to my terminal and typed the usual; sudo synaptic, hit enter, and received this message: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
The same happened when I went to sudo apt-get update, when I went to my update manager, and tried sudo apt-get autoremove. 
I honestly have no idea of where to go from here, as I am not all that good with fixing problems myself, I usually cause two while fixing one. Anyway, If you know how to fix this, It would be very helpful if you were to post it. Thank you.

---

### Post by scragar on 2008-07-20
run```
sudo dpkg --configure -a
```

dpkg has had a bit of a problem and needs to check all it's settings and such, so run that and leave it to check the packages installed etc, it'll stop eventualy and you'll be able to use synaptic etc again.

---

### Post by drs305 on 2008-07-20
Did you run:
```
sudo dpkg --configure -a
```

If so and you still get the error, if you run the following does your host file look ok:
```
cat /etc/hosts
```

It should include a line without any additional info tagged onto the username:
127.0.1.1 username

---

### Post by ~Nightingale~ on 2008-07-20
Thank you all, My problem is fixed.

---


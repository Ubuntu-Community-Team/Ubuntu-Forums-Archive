---
title: "chmod 700 / (Oops!)"
date: 2008-10-12
forum: General Help
---

### Post by sdlyr8 on 2008-10-12
I accidentally typed "chmod 700 /" instead of "chmod 700 ." (damn new keyboard!) and now obviously that really messed somethings up! what's it supposed to be at and/or how should i go about fixing this?

Thanks!

---

### Post by sokopok on 2008-10-12
This should do the trick:
```
chmod 0755 /
```

---

### Post by louieb on 2008-10-12
At least you did not use the recursive option. That would have lead to a reinstall. 
But the Default for the / directory is 755.  You should be able to chmod it back.

755 is read write execute for root 
everybody else gets read and execute.

---

### Post by sdlyr8 on 2008-10-12
Alright thanks guys! I had it as 777 as a temporary fix but I knew that wasn't right and I wanted to make sure it was back to normal. 

And yeah no kidding! That would have been disastrous!

---


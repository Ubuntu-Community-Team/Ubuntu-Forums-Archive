---
title: "Profiling tools"
date: 2009-02-05
forum: Hardware
---

### Post by hRob on 2009-02-05
I am running Intrepid and I would want to profile my processor.. I want to read the cache variations and analyze hit/miss ratio and stuff like that.. I also want to monitor the MPI calls and transfer of data over the network and stuff like that.. **I dont want to use valgrind**.. please tel me something else.. soemthing that will gimme lots more details..

---

### Post by hRob on 2009-02-05
i need help with this here.. can someone gimme a good suggestion?? i need it for a project that i am currently working on right now..

---

### Post by sdennie on 2009-02-05
If I remember correctly, all those tools do different things.  If you are interested in MPI statistics I think vampir is probably your best bet on linux.  If you are interested in cache information, I think valgrind and using kcachegrind to analyze the data is a very good method (kcachegrind is fantastic once you understand what it's trying to tell you).

---

### Post by hRob on 2009-02-06
sweet niblets!! thats precisely wat i wanted!! thnx a ton! I will start working on it immediately..

---


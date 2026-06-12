---
title: "Lost Session Instances for a user on crash how to get back?"
date: 2008-09-29
forum: General Help
---

### Post by timZZ on 2008-09-29
Hi,

I am currently running **Ubuntu 8 Hardy** I am using **FreeNX** to communicate without a monitor / Keyboard / Mouse to my server.

At the moment I am diagnosing a problem where my FreeNX client freezes and I am not able to recover it.

Here is my question.

When I start FreeNX back up it will tell me things like "There is another application running please shut that down first before starting another" (Not a direct quote)

So I know another instance of my login is in session.

I resolve this problem by using the killall command in the terminal. (whether right or wrong I don't know)

**But is there any way of seeing what sessions are currently being used on the server so I may shut them down to reserve resources?**

---

### Post by timZZ on 2008-09-29
Basically how I am resolving this issue now is Periodically I am just restarting the server via the terminal.

But basically I am looking to control/see all the instances for 1 user as I would imagine I have many instances for 1 user in session which my FreeNX cannot retrieve.

---

### Post by timZZ on 2008-09-29
Bump

---

### Post by timZZ on 2008-09-30
So I have learned about the users command in terminal and what I can assume is happening is after a certain period of inactivity the account is simply logged out.

But when I crashed I ran users and I saw the account twice.

I don't know how to log an instance of a user but I am able to log both of the repeated user out via the terminal.

---


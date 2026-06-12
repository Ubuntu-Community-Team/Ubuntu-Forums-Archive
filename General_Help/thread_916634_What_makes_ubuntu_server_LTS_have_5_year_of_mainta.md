---
title: "What makes ubuntu server LTS have 5 year of maintanence"
date: 2008-09-11
forum: General Help
---

### Post by TheR on 2008-09-11
I am having troubles instaling ubuntu server from cd on virtialized xen 3.2. standard server. Instalation hangs on first screen. Keyboard does not respond at all.

But I was able to install kernel-virtual mode from mini-CD version in cli-expert mode (kernel-server has lots of problems).

Since I plan to run some realtime applications on the server I would like to have 5 year (LTS) support for my virtual machines.

So my question is what makes server edition have 5 years maintanance support and can this be acomplished for any ubuntu edition (desktop, virtual ..)

by
TheR

---

### Post by Sef on 2008-09-11
There are normal versions which are supported for 18 months.   Now, it has been decided that long term support versions will come out every two years.  Mark Shuttleworth, the owner of Canonical, has the final word on if something is a LTS or not.  For example, Ubuntu 8.04 has LTS, but Kubuntu 8.04 does not.

---

### Post by TheR on 2008-09-11
> **Sef said:**
> There are normal versions which are supported for 18 months.   Now, it has been decided that long term support versions will come out every two years.  Mark Shuttleworth, the owner of Canonical, has the final word on if something is a LTS or not.  For example, Ubuntu 8.04 has LTS, but Kubuntu 8.04 does not.

Yeah. OK. I understand that. But how does computer differ LTS repositories from non LTS repositories. In the same Ubuntu version (mine is 8.04), to be clear.

by
TheR

---

### Post by kpkeerthi on 2008-09-11
The repositories are the same for all 8.04 variants (ubuntu, kubuntu, server). But only the server packages will receive security updates for 5 years. Kubuntu packages will not.

---


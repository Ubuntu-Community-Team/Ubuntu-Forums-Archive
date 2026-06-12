---
title: "100% cpu usage 3 out of 4 computers"
date: 2009-05-19
forum: Hardware
---

### Post by jc_anthro on 2009-05-19
OK, this is giving me the willies. Three of my four computers have an issue with constant 100% or near cpu usage, which makes them virtually impossible to use.

The affected computers are:

IBM thinkpad P3 (M) running Jaunty (1 meg ram)
Toshiba sattellite P4 running Hardy (1 meg ram)
Asus eeepc running easy peasy (hardy) (1 meg ram)
my Dell running hardy and with roughly the same software set as all my other computers (and I don't run anything weird) sits on around 3-4%. None of the computers is maxing on ram usage or swaps.

Looking at a range of other threads out there and the bug track there is a persistent pattern of this problem, but I haven't seen an effective solution. I think there is a general view that it is a kernel problem or something in gnome (but easy peasy is not gnome so that doesn't really follow).

I've tried using a cpu limiter but that just kills everything (suggesting the CPU hog processes are a symptom not a cause).

Can anybody out there help me? Please......

---

### Post by SteveDee on 2009-05-20
> **jc_anthro said:**
> OK, this is giving me the willies. Three of my four computers have an issue with constant 100% or near cpu usage, which makes them virtually impossible to use.

The affected computers are:

IBM thinkpad P3 (M) running Jaunty (1 meg ram)
Toshiba sattellite P4 running Hardy (1 meg ram)
Asus eeepc running easy peasy (hardy) (1 meg ram)
my Dell running hardy and with roughly the same software set as all my other computers (and I don't run anything weird) sits on around 3-4%. None of the computers is maxing on ram usage or swaps.

Looking at a range of other threads out there and the bug track there is a persistent pattern of this problem, but I haven't seen an effective solution. I think there is a general view that it is a kernel problem or something in gnome (but easy peasy is not gnome so that doesn't really follow).

I've tried using a cpu limiter but that just kills everything (suggesting the CPU hog processes are a symptom not a cause).

Can anybody out there help me? Please......

So which process is consuming 100%cpu time?  {System Monitor > Processes > View > All Processes}

---

### Post by Romala on 2009-05-20
There is the same problem. The process is Firefox. The solution is to switch off Java: Firefox->Settings.

---

### Post by SteveDee on 2009-05-21
> **Romala said:**
> There is the same problem. The process is Firefox. The solution is to switch off Java: Firefox->Settings.

...I have Java enabled on Firefox 3.0.10 but don't get this problem on any of my 3 'buntu desktop PCs.

---


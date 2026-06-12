---
title: "A quick question about mono"
date: 2008-11-15
forum: General Help
---

### Post by Grant A. on 2008-11-15
Is Mono installed by default in Kubuntu Intrepid Ibex 8.10?

---

### Post by ju2wheels on 2008-11-16
Maybe, but only partially. Some applications may use mono libraries (fspot, mysql etc have a few dependencies tied to mono libs) and thus those libraries would be installed in your system. The Mono development tools however will most likely not be installed by default.

---

### Post by loell on 2008-11-16
I doubt kubuntu uses mono components, mysql have no mono components either.

---

### Post by ju2wheels on 2008-11-16
> **loell said:**
> I doubt kubuntu uses mono components, mysql have no mono components either.

Incorrect: libmono-system-data2.0-cil lists libmysql5.0-cil as a library that depends on it, shown below. So as I stated MySQL, and F-spot have libraries that depend on or directly depend on mono libs.

[[IMG]http://img201.imageshack.us/img201/725/screenshotnc8.png[/IMG]](http://imageshack.us)

---

### Post by directhex on 2008-11-16
> **ju2wheels said:**
> Incorrect: libmono-system-data2.0-cil lists libmysql5.0-cil as a library that depends on it, shown below. So as I stated MySQL, and F-spot have libraries that depend on or directly depend on mono libs.

[[IMG]http://img201.imageshack.us/img201/725/screenshotnc8.png[/IMG]](http://imageshack.us)

1) libmysql5.0-cil is a managed (i.e. .NET) library, it is not required by MySQL in any way (it is required for CLI apps to work WITH MySQL)

2) F-Spot is all well and good, but it's not installed in Kubuntu, which this thread si about

---

### Post by loell on 2008-11-16
> **directhex said:**
> 1) libmysql5.0-cil is a managed (i.e. .NET) library, it is not required by MySQL in any way (it is required for CLI apps to work WITH MySQL)

2) F-Spot is all well and good, but it's not installed in Kubuntu, which this thread is about

this is the complete explanation of what i meant. :lol:

---

### Post by ju2wheels on 2008-11-16
And that is what I meant when I said it was required by the applications libraries (libmysql5.0-cil) or the application itself directly (f-spot). Just didnt make that as clear in my wording.

And yes, I agree it F-spot is not installed in Kubuntu which is why I stated in my original post "Maybe, but only partially" as the OP may have installed applications after the fact that use the mono libs.

So we are all correct, depending on the OP's current circumstance... :)

---

### Post by directhex on 2008-11-16
> **ju2wheels said:**
> So we are all correct, depending on the OP's current circumstance... :)

Nope, the answer to "Is Mono installed by default in Kubuntu Intrepid Ibex 8.10?" is an unequivocal "NO". No grey areas, just "NO"

---


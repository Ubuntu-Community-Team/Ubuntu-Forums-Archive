---
title: "Ubuntu shows dual-core, but i only have one"
date: 2011-04-27
forum: Hardware
---

### Post by wordup on 2011-04-27
Hello, i installed ubuntu netbook edition on my Asus EeePC 1005PX which has afaik only one core. The cpu chronis of ubuntu shows 2 cores with different usage.. why??

---

### Post by jespdj on 2011-04-27
According to the specs that I found somewhere that Eee PC model has an [Intel Atom N450](http://ark.intel.com/Product.aspx?id=42503) processor.

According to the specs that processor has 1 core but it can handle 2 threads at a time (because it has [hyper-threading](http://en.wikipedia.org/wiki/Hyper-threading)). In your operating system, it will appear as if it has 2 cores because of this.

---

### Post by wordup on 2011-04-27
Makes sense ;) Thank you!

---


---
title: "Using power status trigger"
date: 2012-01-18
forum: Hardware
---

### Post by bipin.nag on 2012-01-18
I wanted to use the power status of my laptop in  my programs
like how do I use power status to trigger some actions

For example
if power status changes from charging to battery start/stop a service
or if battery power falls below some percentage sleep

NOT that i want to make some power manager for my system
just take the inputs from the power status to do stuff in form of bash scripts

---

### Post by SteveDee on 2012-01-18
> **bipin.nag said:**
> I wanted to use the power status of my laptop in  my programs...

Well you could look at: /proc/acpi/ac_adapter/AC/state
which may look something like this:-
```

state:                   off-line

```
...when on battery, or this:-
```

state:                   on-line

```
...when running from the charger.

---

### Post by bipin.nag on 2012-01-19
Thanks that is what I was looking for

---


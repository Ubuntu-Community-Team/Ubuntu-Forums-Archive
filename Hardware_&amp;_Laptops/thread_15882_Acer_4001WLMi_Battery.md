---
title: "Acer 4001WLMi Battery"
date: 2005-02-17
forum: Hardware &amp; Laptops
---

### Post by zon7 on 2005-02-17
Hi.
Maybe it has been posted before, or with the lattest Hoary it's been solved, but I can't manage to make it work.
The Ubuntu system doesn't detect my battery so I don't know how much is left.
Tried ACPI=true or something like that (can't remember what it was cause I've got exams after that :D ) and it didn't work.
Anyone has solved it?
Thanks

---

### Post by snop on 2005-02-17
[QUOTE=zon7]Hi.
Maybe it has been posted before, or with the lattest Hoary it's been solved, but I can't manage to make it work.
The Ubuntu system doesn't detect my battery so I don't know how much is left.
Tried ACPI=true or something like that (can't remember what it was cause I've got exams after that :D ) and it didn't work.
Anyone has solved it?
Thanks[/QUOTE]
 Hi,

It uses a smart battery. Smart batteries are not yet supported by linux but support is being implemented (check acpi linux mailing list for more info: [http://lists.sourceforge.net/lists/listinfo/acpi-devel](http://lists.sourceforge.net/lists/listinfo/acpi-devel)).

Also, you can check this pages about Travelmate 4001 and linux:
[http://www.squirrel.nl/people/jvromans/articles/TM4001WLMi/fedora.html](http://www.squirrel.nl/people/jvromans/articles/TM4001WLMi/fedora.html)

Hope this helps.

Bye

PD: A couple of solutions are available. Check mailing lists to now more about this. They are not yet officialy merged into the kernel.

---

### Post by KrIaXPaTaLa on 2005-05-05
Check [http://www.ubuntuforums.org/showthread.php?t=29412&highlight=acer+battery](http://www.ubuntuforums.org/showthread.php?t=29412&highlight=acer+battery)

Worked for me.

Best regards,

Kriax, Portugal.

---


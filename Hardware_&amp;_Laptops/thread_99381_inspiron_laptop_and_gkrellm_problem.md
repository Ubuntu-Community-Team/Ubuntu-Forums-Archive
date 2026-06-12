---
title: "inspiron laptop and gkrellm problem"
date: 2005-12-05
forum: Hardware &amp; Laptops
---

### Post by Houman on 2005-12-05
Hello everyone;

I have breezy on a 6000 inspiron, I noticed that the fan was almost always runnin on maximum which was annoying because the fan is pretty noisy;

Im not sure how the default breezy controls the fan (powernowd?) but i decided to install the gkrellm with the i8k (dell laptop plugin) to both minotor the temperature and control the fans in a sensible manner (these programs are all in the repo)

however i get these message at boot:
```
i8k: not running on a Dell system
i8k: vendor=Dell Inc., model=Inspiron 6000, version=A09
i8k: unable to get SMM Dell signature
i8k: unable to get SMM BIOS version

```
and i googled around and found this site : [http://www.wayfinder.it/resources/inspiron8500.php]("http://www.wayfinder.it/resources/inspiron8500.php") where the author gets the same messages and claims the temperature reported is incorrect, 

I was wondering should i uninstall the i8k plugin? is it throttling the fans based  on incorrect temperature? could this damage my laptop? also I was wondering what other inspiron owners do about the fan problem?

appreciate any comments;
Houman

---

### Post by markr on 2005-12-06
I'm running on an Inspiron 5150 and must admint that I've not seen any temperature issue.  Doing an "acpi -V" reports 52 degress C.

Reading through the forums though I'm a bit worried that this is not reporting correctly.

I'm going to install the i8k stuff and see how that goes.

---


---
title: "error Need a server with input ABI 12"
date: 2010-12-11
forum: Hardware
---

### Post by kingpinzs on 2010-12-11
What in the world does that mean when trying to complie a driver?

---

### Post by kingpinzs on 2010-12-12
Still can not find what input ABI 12 means. Any one know?

---

### Post by kingpinzs on 2010-12-17
So I am geussing nobody knows what the error "Need a server with input ABI 12" means when compiling the fpit driver?
 
This is where the code is erroring out.
 
#if GET_ABI_MAJOR(ABI_XINPUT_VERSION) < 12
#error "Need a server with input ABI 12"
#endif
 
as far as I know it has the latest xinput
 
how do i check the version?

---


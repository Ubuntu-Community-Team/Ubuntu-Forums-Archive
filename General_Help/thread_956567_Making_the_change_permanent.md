---
title: "Making the change permanent"
date: 2008-10-23
forum: General Help
---

### Post by Ironhorse_somo on 2008-10-23
I had a previous problem solved by this method:

Try to use the kernel boot options "all_generic_ide" .
Follow this guide as to how to input the parameter: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
substitute the "quiet splash --" and add "all_generic_ide" (without the quotes)


What I'm looking to do now is to make that change permanent, so I don't have to go in and edit the kernel every time the computer boots up. Help?

---

### Post by jeenuv on 2008-10-23
> **Ironhorse_somo said:**
> I had a previous problem solved by this method:

Try to use the kernel boot options "all_generic_ide" .
Follow this guide as to how to input the parameter: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
substitute the "quiet splash --" and add "all_generic_ide" (without the quotes)


What I'm looking to do now is to make that change permanent, so I don't have to go in and edit the kernel every time the computer boots up. Help?
Isn't there a section named "Change Boot Options Permanently On An Existing Ubuntu System" on the same page? Isn't it what you're looking for?

---

### Post by Ironhorse_somo on 2008-10-23
*Smacks forehead and marks thread solved* Thank you :)

---


---
title: "Java Update Broke my MATLAB GUI"
date: 2008-10-14
forum: General Help
---

### Post by Doughy on 2008-10-14
I just updated Java through the update manager, only to find that it broke my MATLAB GUI.  Now, when I try to start matlab, the Matlab splash screen appears, then disappears, and matlab falls back to the command line version.  Anyone know how to fix this?

Thanks.

---

### Post by ju2wheels on 2008-10-14
Your java might not be properly configured after the update and may be falling back on the open source java instead of the Sun version and thus causing you problems.

Try the instructions I posted in this thread first: [http://ubuntuforums.org/showthread.php?t=946573](http://ubuntuforums.org/showthread.php?t=946573)

If that doesnt work then post back. I dont recall having to change anything else to make Matlab work.

---

### Post by Doughy on 2008-10-16
> **ju2wheels said:**
> Your java might not be properly configured after the update and may be falling back on the open source java instead of the Sun version and thus causing you problems.

Try the instructions I posted in this thread first: [http://ubuntuforums.org/showthread.php?t=946573](http://ubuntuforums.org/showthread.php?t=946573)

If that doesnt work then post back. I dont recall having to change anything else to make Matlab work.

No, didn't work.  Thanks for the suggestion though.

---

### Post by meandstuff on 2008-11-17
I have a similar problem, although my GUI never did work.  I suspect that matlab is looking at the wrong java jre, but I haven't figured out how to change that.  Anyone have ideas?

N.

---

### Post by Doughy on 2008-11-18
> **meandstuff said:**
> I have a similar problem, although my GUI never did work.  I suspect that matlab is looking at the wrong java jre, but I haven't figured out how to change that.  Anyone have ideas?

N.

It turns out that if you have certain versions of matlab, you need to add an environment variable so that matlab knows where to find java.  I added this line:

```
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.07/jre
```

You may need to change that line based on what version of java you have.  Let me know if it works.

---

### Post by Cyberto on 2010-09-27
have the same Problem but Doughys solution didn't work....

---


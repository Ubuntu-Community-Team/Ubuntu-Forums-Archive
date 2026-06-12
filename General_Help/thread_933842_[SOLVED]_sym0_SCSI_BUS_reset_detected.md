---
title: "[SOLVED] sym0: SCSI BUS reset detected"
date: 2008-09-29
forum: General Help
---

### Post by tad1073 on 2008-09-29
What is this all about, and how do I fix it? This happens evertime I boot.

```
Sep 29 12:43:30 hp kernel: [   53.973614] sym0: SCSI BUS reset detected.
Sep 29 12:43:30 hp kernel: [   54.002131] sym0: SCSI BUS has been reset.
Sep 29 12:43:30 hp kernel: [   87.489154] sd 0:0:1:0: [sdb] ABORT operation started
Sep 29 12:43:30 hp kernel: [   92.506653] sd 0:0:1:0: ABORT operation timed-out.
Sep 29 12:43:30 hp kernel: [   92.530142] sd 0:0:1:0: [sdb] ABORT operation started
Sep 29 12:43:30 hp kernel: [   97.548149] sd 0:0:1:0: ABORT operation timed-out.
Sep 29 12:43:30 hp kernel: [   97.571486] sd 0:0:0:0: [sda] ABORT operation started
Sep 29 12:43:30 hp kernel: [  102.589646] sd 0:0:0:0: ABORT operation timed-out.
Sep 29 12:43:30 hp kernel: [  102.612985] sd 0:0:2:0: [sdc] ABORT operation started
Sep 29 12:43:30 hp kernel: [  107.631143] sd 0:0:2:0: ABORT operation timed-out.
Sep 29 12:43:30 hp kernel: [  107.654335] sd 0:0:2:0: [sdc] ABORT operation started
Sep 29 12:43:30 hp kernel: [  112.672643] sd 0:0:2:0: ABORT operation timed-out.
Sep 29 12:43:30 hp kernel: [  112.695371] sd 0:0:0:0: [sda] DEVICE RESET operation started
Sep 29 12:43:30 hp kernel: [  117.714138] sd 0:0:0:0: DEVICE RESET operation timed-out.
Sep 29 12:43:30 hp kernel: [  117.736871] sd 0:0:1:0: [sdb] DEVICE RESET operation started
Sep 29 12:43:30 hp kernel: [  122.755635] sd 0:0:1:0: DEVICE RESET operation timed-out.
Sep 29 12:43:30 hp kernel: [  122.778472] sd 0:0:2:0: [sdc] DEVICE RESET operation started
Sep 29 12:43:30 hp kernel: [  127.797134] sd 0:0:2:0: DEVICE RESET operation timed-out.
Sep 29 12:43:30 hp kernel: [  127.819934] sd 0:0:1:0: [sdb] BUS RESET operation started
Sep 29 12:43:30 hp kernel: [  127.844831] sym0: SCSI BUS reset detected.
Sep 29 12:43:30 hp kernel: [  127.871640] sym0: SCSI BUS has been reset.
Sep 29 12:43:30 hp kernel: [  127.893793] sd 0:0:1:0: BUS RESET operation complete.
```

---

### Post by tad1073 on 2008-09-30
bump

---

### Post by svinx on 2010-04-28
I seem to be having the same problem. 
any resolution for this issue? This thread appears to be considered 'SOLVED', but no solution is here..

---


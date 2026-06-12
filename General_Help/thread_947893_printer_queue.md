---
title: "printer queue"
date: 2008-10-14
forum: General Help
---

### Post by godotub on 2008-10-14
Can someone advise me how to erase a printer queue.
Being a complete novice please give it step by step.

Thanks in anticipation

Godotub.

---

### Post by unutbu on 2008-10-14
Open a terminal ([http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)) and type
```

lpq
```

Do you see a list of print jobs?
If so, you can remove a job by typing
```

lprm JOB_NUMBER
```

or, to remove all print jobs,
```

lprm -
```

---

### Post by godotub on 2008-10-18
Many thanks to UNUTBU.

Worked a treat. Saves a potential waste of ink and paper.

Godotub.

---


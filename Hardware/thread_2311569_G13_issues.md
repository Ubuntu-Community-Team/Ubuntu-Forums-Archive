---
title: "G13 issues"
date: 2016-01-28
forum: Hardware
---

### Post by steck638 on 2016-01-28
So I did do a fair amount of research before posting this. I found another couple threads about G13 game pads, found a driver and got kind of excited thinking it would just work, learned a bit about the make program, and well hit a brick wall. I am sure its just something I dont know, but I keep getting this for an output.
```
/home/steck/Untitled/Makefile: 1: /home/steck/Untitled/Makefile: EXE_NAME: not found/home/steck/Untitled/Makefile: 2: /home/steck/Untitled/Makefile: SRC_DIR: not found
/home/steck/Untitled/Makefile: 3: /home/steck/Untitled/Makefile: SRC_DIR: not found
/home/steck/Untitled/Makefile: 3: /home/steck/Untitled/Makefile: SRC_DIR: not found
/home/steck/Untitled/Makefile: 3: /home/steck/Untitled/Makefile: SRC_DIR: not found
/home/steck/Untitled/Makefile: 3: /home/steck/Untitled/Makefile: SRC_DIR: not found
/home/steck/Untitled/Makefile: 3: /home/steck/Untitled/Makefile: SRC_DIR: not found
/home/steck/Untitled/Makefile: 3: /home/steck/Untitled/Makefile: SRC_DIR: not found
/home/steck/Untitled/Makefile: 3: /home/steck/Untitled/Makefile: SRC_DIR: not found
/home/steck/Untitled/Makefile: 3: /home/steck/Untitled/Makefile: OBJS: not found
/home/steck/Untitled/Makefile: 4: /home/steck/Untitled/Makefile: CC: not found
/home/steck/Untitled/Makefile: 5: /home/steck/Untitled/Makefile: FLAGS: not found
/home/steck/Untitled/Makefile: 6: /home/steck/Untitled/Makefile: LIBS: not found
/home/steck/Untitled/Makefile: 8: /home/steck/Untitled/Makefile: EXE_NAME: not found
/home/steck/Untitled/Makefile: 8: /home/steck/Untitled/Makefile: all:: not found
/home/steck/Untitled/Makefile: 10: /home/steck/Untitled/Makefile: .cpp.o:: not found
/home/steck/Untitled/Makefile: 11: /home/steck/Untitled/Makefile: CC: not found
/home/steck/Untitled/Makefile: 11: /home/steck/Untitled/Makefile: FLAGS: not found
/home/steck/Untitled/Makefile: 11: /home/steck/Untitled/Makefile: cannot open -o: No such file
/home/steck/Untitled/Makefile: 11: /home/steck/Untitled/Makefile: -c: not found
/home/steck/Untitled/Makefile: 13: /home/steck/Untitled/Makefile: EXE_NAME: not found
/home/steck/Untitled/Makefile: 13: /home/steck/Untitled/Makefile: OBJS: not found
/home/steck/Untitled/Makefile: 14: /home/steck/Untitled/Makefile: CC: not found
/home/steck/Untitled/Makefile: 14: /home/steck/Untitled/Makefile: OBJS: not found
/home/steck/Untitled/Makefile: 14: /home/steck/Untitled/Makefile: EXE_NAME: not found
/home/steck/Untitled/Makefile: 14: /home/steck/Untitled/Makefile: FLAGS: not found
/home/steck/Untitled/Makefile: 14: /home/steck/Untitled/Makefile: LIBS: not found
/home/steck/Untitled/Makefile: 14: /home/steck/Untitled/Makefile: -o: not found

```
Now I dont know a lot about linux, just trying to get my game pad to work, I had the Makefile in the same folder as the folder with some files in it (constants.h G13.cpp G13.h G13Action.cpp G13Action.h Macro.cpp Macro.h MacroAction.cpp MacroAction.h Main.cpp Output.cpp Output.h PassThroughAction.cpp and PassThroughAction.h) and then I tried moving them all to the same folder as the Makefile thinking it couldnt find them in a sub folder. Then I extracted the jar into the folder thinking it might not be able to find that. It still failed and I am sure I just dont know what I am doing... but I cant seem to get it to work, its late and I am tired.

---


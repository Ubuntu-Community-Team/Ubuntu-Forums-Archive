---
title: "Got problems while compiling XBOX360 controller driver........"
date: 2008-11-06
forum: Hardware
---

### Post by Shinwar on 2008-11-06
I'v seen this post and did it as he said.
[http://ubuntuforums.org/showthread.php?t=825464&highlight=xbox+controller](http://ubuntuforums.org/showthread.php?t=825464&highlight=xbox+controller)
but I'm puzzled about this.
Help,plz.........

scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o helper.o -c -g -O0 -Wall helper.cpp
g++ -o uinput.o -c -g -O0 -Wall uinput.cpp
uinput.cpp: In constructor 'uInput::uInput(GamepadType, uInputCfg)':
uinput.cpp:45: error: 'strerror' was not declared in this scope
uinput.cpp:59: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:59: error: 'exit' was not declared in this scope
uinput.cpp:74: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:74: error: 'exit' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_gamepad(GamepadType)':
uinput.cpp:148: error: 'memset' was not declared in this scope
uinput.cpp:149: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_guitar()':
uinput.cpp:233: error: 'memset' was not declared in this scope
uinput.cpp:234: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_button(uint16_t, int32_t)':
uinput.cpp:260: error: 'memset' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_axis(uint16_t, int32_t)':
uinput.cpp:274: error: 'memset' was not declared in this scope
scons: *** [uinput.o] Error 1

---

### Post by Shinwar on 2008-11-06
Oops, Version BUGs,killed it .

---

### Post by ajhtiredwolf on 2008-11-06
Were you able to fix this then?

---


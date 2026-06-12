---
title: "houdini apprentice wont start"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by alnoth on 2009-02-15
i just installed houdini apprentice, the installation went fine. when i try to run it tho, it doesnt start and it produces a crash report, which reads:

Crash report from erik; Unknown App Version 9.5.350 [linux-i686-gcc4.1]
Traceback from Sun Feb 15 14:08:42 2009
Caught signal 11
AP_Interface::coredumpHandler(UTsignalHandlerArg) (??:0)
UT_Signal::processSignal(int, siginfo*, void*) (??:0)
__glXGetStringFromServer (??:0)
__glXGetStringFromServer (??:0)
glXMakeCurrent (??:0)
RE_XServer::GLMakeCurrent(unsigned long, void*) (??:0)
RE_Window::makeCurrent(bool&) (??:0)
RE_XWindow::makeCurrent(bool&) (??:0)
RE_OGLRender::makeWindowCurrent(RE_Window*) (??:0)
RE_OGLRender::setContext(RE_Window*, int) (??:0)
RE_OGLRender::pushContext(RE_Window*) (??:0)
RE_GenWindow::winopen(char const*, bool, bool, bool) (??:0)
RE_RasterWindow::begin(int, int, PXL_DataFormat, bool) (??:0)
RE_RasterObject::buildOffscreen() (??:0)
RE_RasterObject::build() (??:0)
UI_LookTextureCache::buildNewLooks() (??:0)
UI_Window::doRedraw() (??:0)
UI_Queue::doWindowRedraws() (??:0)
UI_Timer::handleEvent(UI_Event*) (??:0)
UI_Queue::processNextEvent() (??:0)
UI_Queue::drain() (??:0)
UI_Queue::eventLoop() (??:0)
main_part2(int, char**) (AP_Main.C:0)
main (??:0)

any idea what may be the problem here? :(

---


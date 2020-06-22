---
title: Invitation
linktitle: Invitation
toc: true
type: docs
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  example:
    parent: Beginner Quest
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1
---

You are a simple life form, exiled from your home planet and in search of a new place to call home. The ruling came fast. Your taste in music was deemed to be far too "out-there-man" for anyone to possibly associate with you anymore. You were given 60 revolutions of Xenon around Fir to leave and never return. Gather whatever possessions and leave. You find your parents music collection, oddly in it is a golden disc labelled "Property of NASA, if lost please return to: EVNJAKL 1600 Ampitheatre Parkway Mountain View California." The music on the disc was uncovered a while back and was not very interesting. This weird language that said something about "Peace, love and rock and roll. Also we're having a really cool party tonight, so for whoever is out there, bring a friend and come along! Co-ordinates enclosed." On the back the words "Draft, do not distribute or load onto probe" written in big red letters. That could mean anything.

You'll go, since you have nowhere else to go. But you'll be careful. You well know to learn all you can about alien beings before making contact. They could be hostile, or listen to boring music. Time is slipping away fast, you race aboard the nearest ObarPool Spaceship. But you've never driven one... what next genius?

## Task: Enter Space-Time Coordinates (Misc)

Ok well done. The console is on. It's asking for coordinates. Beating heavily on the console yields little results, but the only time anything changes on your display is when you put in numbers.. So what numbers are you going to go for?  You see the starship's logs, but is there a manual? Or should you just keep beating the console?

[Task Files](https://storage.googleapis.com/gctf-2019-attachments/00c2a73eec8abb4afb9c3ef3a161b64b451446910535bfc0cc81c2b04aa132ed)

## Solution

Go ahead and download the Task Files and navigate to the folder in your command line client (I'll be using Linux). Using the `ls` command, we'll list out the files to determine what we have to work with. In this task, we are given two files: a .txt file and an executable binary.

{{< figure library="true" src="googlectf2019/001invitation/sol1.png" title="List out files using ls" lightbox="true" >}}

Let's go ahead and check what is in the text file. We'll use the `cat` command to print out the contents of the text tile to the console. Unfortunately, there does not seem to be anything of note here. 

{{< figure library="true" src="googlectf2019/001invitation/sol2.png" title="Run CAT output of log.txt" lightbox="true" >}}

Next, we will go ahead and execute the binary(If you do not have execute permission, run the following command `chmod +x`). It looks like this binary is the menu interface for the spaceship. Incidentally, the CTF destination is redacted and we get an error message when we input coordinates.

{{< figure library="true" src="googlectf2019/001invitation/sol3.png" title="Run the binary file" lightbox="true" >}}

Exit out of the program with `^c`. Let's see if we can brute force the flag out of the binary by running the `strings` command on the `./rand2` binary. This technique allows us to parse out the plain text from a binary file. We see that there are plenty of plain text strings within this file, so we need a fast way to search through. 

{{< figure library="true" src="googlectf2019/001invitation/sol4.png" title="Run strings" lightbox="true" >}}

Fortunately, GREP will come to the rescue. We'll pipe the output of strings into grep input using the following command `strings ./rand2 | grep flag`. There is our flag!

{{< figure library="true" src="googlectf2019/001invitation/sol5.png" title="Grep the strings output" lightbox="true" >}}

Flag:  `CTF{welcome_to_googlectf}`

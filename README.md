# PWGEN on Alpine linux

## Software
This repository can be used to generate an alpine linux based docker image for strong GPL'ed password generation using "pwgen" software.
The [package](https://pkgs.alpinelinux.org/package/main/x86_64/pwgen) is on the alpine repo under GPL License. For all the possible options on the pwgen software, please have a look at this [manual](http://linux.die.net/man/1/pwgen).

## Base image
I use the Alpine Linux base image as one of the smallest base images with a repository (as far as I know, at the time of writing). The goal is to avoid heavy "usual" ubuntu/debian base image to install one utility software. The final result is less than 5MB total in size.
```
REPOSITORY              TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
gliderlabs/alpine       3.3                 24e7cde1dbe9        7 weeks ago         4.794 MB
pwgen                   alp                 1561045d53be        22 minutes ago      4.835 MB
```

## Possible use
Please use as you please in any project of yours as you see fit. For example, as a utility software to install on coreos and use for other services initialisations.
If you want to include this software in you project, one inspiration could be the "run.sh" file in the public repository of the tutum mysql image.


## How to use this repository
Standard git clone command and docker build, provided with an example to generate **3 secure passwords of 15 characters with special symbols separated by a space/blank delimiter**. Note that as of recent Docker security recommendations, the "nobody" non-root user is the one invoking the pwgen command inside your container. See [here](https://www.youtube.com/watch?v=LmUw2H6JgJo).

```
git clone https://github.com/sofianinho/pwgen-alpine.git
cd pwgen-alpine
docker build --tag=pwgen:alp .
docker run -t pwgen:alp -sy 15 3
WY~4-Psy;Kqb]r^ >]`k60@d.2LVuo~ s"?siy-J4yM;TYj 

```
## License
![MIT license](LICENSE.md). Use as you please.

# C-Spec primer

## Introduction

In the software industry there is a massive shift towards containers and Kubernetes. 

This is a very exciting space to be working in. But it is equally challenging!

I recently saw a KubeCon session that talks about [building docker containers without docker by Matt Rickard](https://youtu.be/qhykcC94ukg). It also talks about creating containers without running commands. Really challenging what we are all doing when creating containers I think.

This talk made me realize that we as an industry are missing a fundamental meta data model to model the software that we are building. 

Here I gather my current ideas of what such a model should comprehend. More details will follow as soon as this idea gains more form in my mind.

## Enter C-Spec

C-Spec stands for command-, configuration- and container-specification.

### Command-specification

We need to be able to model the command line arguments, environment variables and configuration that commands need to run. We also need to model the runtime context, what directory the command itself should be placed, where the configuration is stored, where outputs go. 

We also need to model dependencies. Dependencies in this context are different than the once needed to create the executable. Think of a sound track conversion command. Best case scenario it only requires an MP3 codec when a command line argument specifies it needs to convert to/from MP3.

### Configuration-specification

We need to be able to model configuration. This blends with Command-specifications. This is very challenging because configuration can come from basically anywhere. Additionally this is a really blurry area, with this I mean that this where what configuration lives is mostly very messy. Infrastructure and functional configuration is usually not very well separated in my experience.

But focussing on Kubernetes we want it to come from ConfigMaps, Secrets and environment variables.

If we can model something like the externalized configuration support from [spring-boot](https://docs.spring.io/spring-boot/docs/current/reference/html/boot-features-external-config.html) I will be happy.

### Container-specification

We need to be able to model the configuration a container needs to run. Therefor we need both the command- and configuration-specifications. 

To allow us to describe what configuration values are needed to run the container.

## Why?

If we have such a meta data model. It will allow us to create really smart tooling. 

Creating containers without running commands should be possible and therefor much faster. Containers can also really only contain what is needed.

It should be possible to prevent deploying a new container version because the system knows some configuration is missing or wrong to run this new version.

## Closing

I think this is comparrable of how I think about the evolutions in car manufacturing. In the early days I assume they did not know how many bolts would go into a single car. Today they know exactly everything and how much every component weighs and so on. 

I think we as software industry need to step up and get to the same level.

Thanks for reading. If you have any feedback please drop an issue.

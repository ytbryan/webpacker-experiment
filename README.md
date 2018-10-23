

# The experiment 

Test1 is when yarn add is ran seperately. Test2 is when they are ran together. 

```
test1's result ~> 46.159529
test2's result ~> 27.358681
```

This is an experiment repo I use to decide if it is worthwhile to make a PR to cut the `yarn add` performance time for webpacker. 

Before I begin, I need to ask the folks at webpacker, if they will accept a PR. 

# The proposal

Currently, the installation is broken into separate commands. And separate commands takes up more time. Therefore, I wish to have the command`rails webpacker:install`, install all the dependencies at one go.

How much time? Around 50% bump in time performance. Around 19~20 seconds for each run. 

# Draft in code 

I think people should be able to do the following: 

```
rails webpacker:install something something2 something3
```
And other codes like `rails webpacker:install:vue` should be able to run `yarn add` once and not twice. And for third party library like `vueonrails`, we should be able to leverage this interface to add the dependencies without getting user to pay double time. 

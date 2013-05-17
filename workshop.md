

Development of ToDo Application 
======

```
  rails new todo #initialize a new application
```

```
  cd todo
```

```
  sublime-text-2 . & #start the sublime text with the present folder
```

```
  bundle install #incase of no net, but if you the gems preinstall try 'bundle install --local'
```

To see if the rails application has been initialized properly you can check it by runnung

```bundle exec rails s```

to view the site go to http://localhost:3000

Theme
-----

For view and template we use the twitter bootstrap librar.

To work with bootstrap we require the bootrstrap gem to be placed in the Gemfile 

```gem 'twitter-bootstrap-rails'```

To install the bootstrap files into your system you need to run the following command in the terminal 

```
  bundle exec rails g bootstrap:rails static
```

To install a default bootstrap template to rails we run the following command which the application.html.erb

```
  bundle exec rails g bootstrap:layout fluid
```

Working with static pages
--------------------------

Before we procced to the development of dynamic pages and its contents first lets work with serving static pages. 

To do so we have to generate the controller and actions alone, without adding any code in the controller. Doing so would make the controller just server the view files as it is. 

To generate the controller with its action and default templates, we run the command 

```
  bundle exec rails g controller Site home download about contact
```

Now visitng the link 

```localhost:3000/site/home```

would show a webpage with content

> # Site#home

>Find me in app/views/site/home.html.erb

not to move thse links to a more apropriate location, say rather than localhost:3000/sites/home -> localhost:3000/home. We edit the rotues.rb file which can be found under the config/ folder. 

In routes.rb you will find the following code

>  get "site/home"

>  get "site/download"

>  get "site/about"

>  get "site/contact"

change those codes in routes.rb to ->


>  root to: 'site#home'

>  get '/about', to: 'site#about'

>  get '/download', to: 'site#download'

>  get '/contact', to: 'site#contact'


the structure it follows

```
get/post '<URL>', to: '<CONTROLLER_NAME>#<ACTION_NAME>'
```

Createing Database and Tabes in Rails 
-------------------------------------

To generate a model in ruby, we run the command rails g Model 


>  bundle exec rails g model <MODEL Name> <Column Name>:<Data Type> <Column Name>:<Data Type>

> eg: bundle exec raiks g nidek Task task:string completed:boolean priority:integer


Creating a migration won't make table in do, to make the changes we need to run the migration script.

```bundle exec rake db:migrate```

After migrating the DB, you can try working the data in the DB uthough the console. (A command line interface to ur rails application)

```
  bundle exec rails c
```

To experiment with the model, you can use the following instructions

>Task.create(task:"Complete Workshop",completed:false,priority:2)

>@task = Task.find 1
>@task.update_attributes(complted:true)

>Task.delate_all
>Task.create

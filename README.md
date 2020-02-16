
## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, powerful, and provides tools required for large, robust applications.

## change .env file 
 APP_NAME=<name>
 DB_DATABASE=<name>

 ## change app.php
 timezone' => 'Berlin',
 'locale' => 'en',
 'fallback_locale' => 'en',

##  Routes & Controllers
web.php
 if we add 
 Route::get('/about', function () {
    echo 'hello';
});
 we  can navigate to /about
 it can be a 'post' request to submit form or api etc 
  Route::post ('/about', function () {
    echo 'hello';
});
(1) create controller 
 php artisan make:controller <name>
  - in this case name is homeController
  so open home controller
  and place following code:
  inside the controller

   public function index(){
        return view('welcome');
    }

  (2) replace code in `web.php` with route to controller

   Route::get('/', 'homeController@index');

   ## database migration
   (1) create a model
   php artisan make:model <modelname> 
   eg: php artisan make:model referance 

   (2) create a migration
   `php artisan make:migration <name>`
   eg `php artisan make:migration create_referances_table`
   you can serch this with same name. in file (create_referances_table)
    up : is create table
    down : delete table
    in function `up` we have to define model of table in this senario up function will look like this

      public function up()
    {
        Schema::create('referances', function (Blueprint $table) {
            $table->bigIncrements('id');
            $table->timestamps();
            $table->string('title');
            $table->string('imageUrl');
            $table->string('text');


        });
    }


    (3) create table :
    create a db before with name you configred if its first time
    `php artisan migrate`

    to create table in db

    ## blade template
    create master.blade.php

    use emmet to create html
    and then add 
   ` @yield('content')`
   to body

    create home.blade.php
    add following code
    
    @extends ('master')
@section('title','Homepage')
@section('content')
<h1>hello</h1>
@endsection

and change in controller  from welcome to home\

## date from api

change home controller as folows\


0 9jmnamespace App\Http\Controllers;

use Illuminate\Http\Request;
use App\Referance;

class homeController extends Controller
{
    public function index(){
   $referances= Referance::all();
   foreach($referances as $referance)
   echo $referance->title;


        return view('home');
    }
}


## vuejs 
`composer require laravel/ui --dev`

bootstrap and vue js can be installed with this.
`php artisan ui vue --auth`
after adding this
`npm install`

(2) add file `ExampleComponent.vue` in `resources/js/components`;
(3) register new user


## different backend and frontend file.




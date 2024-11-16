<p align="center">
    <a href="https://github.com/phppress/actions" target="_blank">
        <img src="https://avatars.githubusercontent.com/u/188348450?v=4" height="100px">
    </a>
    <h1 align="center">PHPForge - actions reusable</h1>
    <br>
</p>

## Requeriments

- PHP.

## Usage

### Example of using the [Dependency check](https://github.com/maglnet/ComposerRequireChecker)

```yml
on:
  pull_request:
    paths-ignore:
      - 'docs/**'
      - 'README.md'
      - 'CHANGELOG.md'
      - '.gitignore'
      - '.gitattributes'
      - 'infection.json.dist'
      - 'phpunit.xml.dist'
      - 'psalm.xml'

  push:
    branches: ['main']
    paths-ignore:
      - 'docs/**'
      - 'README.md'
      - 'CHANGELOG.md'
      - '.gitignore'
      - '.gitattributes'
      - 'infection.json.dist'
      - 'phpunit.xml.dist'
      - 'psalm.xml'

name: dependency-check

jobs:
  composer-require-checker:
    uses: phppress/actions/.github/workflows/composer-require-checker.yml@main
    with:
      os: >-
        ['ubuntu-latest']
      php: >-
        ['8.1', '8.2']
```

### Example of using the [Easy Coding Standard](https://github.com/easy-coding-standard/easy-coding-standard)

```yml
on:
  pull_request:
    paths-ignore:
      - 'docs/**'
      - 'README.md'
      - 'CHANGELOG.md'
      - '.gitignore'
      - '.gitattributes'
      - 'infection.json.dist'
      - 'phpunit.xml.dist'

  push:
    branches: ['main']
    paths-ignore:
      - 'docs/**'
      - 'README.md'
      - 'CHANGELOG.md'
      - '.gitignore'
      - '.gitattributes'
      - 'infection.json.dist'
      - 'phpunit.xml.dist'

name: ecs

jobs:
  easy-coding-standard:
    uses: phppress/actions/.github/workflows/ecs.yml@main
    with:
      os: >-
        ['ubuntu-latest']
      php: >-
        ['8.1', '8.2']
```

### Example of using the [Mutation test](https://github.com/infection/infection) action.

```yml
on:
  pull_request:
    paths-ignore:
      - 'docs/**'
      - 'README.md'
      - 'CHANGELOG.md'
      - '.gitignore'
      - '.gitattributes'
      - 'infection.json.dist'
      - 'psalm.xml'

  push:
    branches: ['main']
    paths-ignore:
      - 'docs/**'
      - 'README.md'
      - 'CHANGELOG.md'
      - '.gitignore'
      - '.gitattributes'
      - 'infection.json.dist'
      - 'psalm.xml'

name: mutation test

jobs:
  mutation:
    uses: phppress/actions/.github/workflows/infection.yml@main
    secrets:
      STRYKER_DASHBOARD_API_KEY: ${{ secrets.STRYKER_DASHBOARD_API_KEY }}    
    with:
      # coverage: pcov / coverage: xdebug / coverage: xdebug2 / coverage: none 
      # extensions: ext-php
      # ini-values: date.timezone='UTC'   
      os: >-
        ['ubuntu-latest']
      php: >-
        ['8.1']
      #tools: composer:v2        
```

### Example of using the [Static analysis](https://github.com/phpstan/phpstan) action.

```yml
on:
  pull_request:
    paths-ignore:
      - 'docs/**'
      - 'README.md'
      - 'CHANGELOG.md'
      - '.gitignore'
      - '.gitattributes'
      - 'infection.json.dist'
      - 'psalm.xml'

  push:
    paths-ignore:
      - 'docs/**'
      - 'README.md'
      - 'CHANGELOG.md'
      - '.gitignore'
      - '.gitattributes'
      - 'infection.json.dist'
      - 'psalm.xml'

name: static analysis

jobs:
  psalm:
    uses: phppress/actions/.github/workflows/phpstan.yml@main
    with:
      # extensions: ext-php 
      # ini-values: date.timezone='UTC'       
      os: >-
        ['ubuntu-latest']
      php: >-
        ['8.1', '8.2']
      #tools: composer:v2, cs2pr 
```

### Example of using the [Unit test](https://github.com/sebastianbergmann/phpunit) action.

```yml
on:
  pull_request:
    paths-ignore:
      - 'docs/**'
      - 'README.md'
      - 'CHANGELOG.md'
      - '.gitignore'
      - '.gitattributes'
      - 'infection.json.dist'
      - 'psalm.xml'

  push:
    paths-ignore:
      - 'docs/**'
      - 'README.md'
      - 'CHANGELOG.md'
      - '.gitignore'
      - '.gitattributes'
      - 'infection.json.dist'
      - 'psalm.xml'
  
name: build

jobs:
  phpunit:
    uses: phppress/actions/.github/workflows/phpunit.yml@main
    secrets:
      CODECOV_TOKEN: ${{ secrets.CODECOV_TOKEN }}
    with:
      # coverage: pcov / coverage: xdebug / coverage: xdebug2 / coverage: none 
      # extensions: ext-php 
      # ini-values: date.timezone='UTC'
      # name: my-package      
      os: >-
        ['ubuntu-latest', 'windows-latest']
      php: >-
        ['8.1', '8.2']
      #tools: composer:v2 
```

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

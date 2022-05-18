## Don't believe in myths!

Do you think that only C# version 9.0 onwards supports code generators? .NET Framework projects be darned, Visual Basic the usual disgraced son?

Well, think again.

Code generators are a _compiler_ feature, not a _language_ feature. As long as you build your project with the .NET SDK v6.0 and/or Visual Studio 2022, you can benefit from [incremental generators](https://github.com/dotnet/roslyn/blob/main/docs/features/incremental-generators.md), for example.

(Of course you need to use Roslyn as a compiler; therefore, F# projects are not invited to the party - sorry guys, but hey, your language is so cool you don't even _need_ this kind of stuff, right? :wink:)


Don't believe _me_, either: see for yourself.

### Instructions for Visual Studio

1. Clone this project.
1. Open `CodeGenerationTest.sln` in Visual Studio 2022 (v17.2+ recommended) and build the `CodeGenerators` project.
1. Exit Visual Studio, then open the solution again. This step is needed because VS caches code generators and will not recognize the newly-compiled `CodeGenerators.dll` until you restart it.
1. Open `Program.cs` in the `CSharpApp` project. Verify that there are no errors: both the `Hello` class and its `World` property are present in the assembly, despite this project targeting .NET Framework 4.6.1 (thus, by default, using C# 7.3).
1. Open `Program.vb` in the `VisualBasicApp` project. Verify that there are no errors: both the `Hello` module and its `World` property are present in the assembly, despite this project being in Visual Basic (and, for good measure, explicitly specifying version 15.0 of the language).


### Instructions for .NET SDK

On a computer with .NET SDK v6.0 or later installed:

1. Clone this project.
1. Open the operating system shell of your choice in the folder where you cloned this project.
1. Enter the `dotnet build` command. Verify that there are no errors.
